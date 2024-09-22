# Puppeteer


```js

Puppeteer
│
├── Browser
│   ├── Properties
│   │   ├── isConnected(): boolean  // Checks if browser is connected.
│   │   ├── process(): ChildProcess | null  // Access to the underlying browser process.
│   │   ├── wsEndpoint(): string  // WebSocket endpoint for browser connection.
│   │   ├── target(): Target  // Returns the target associated with the browser.
│   │   ├── targets(): Target[]  // Lists all the targets in the browser.
│   │   ├── userAgent(): Promise<string>  // Retrieves the browser's user agent.
│   └── Methods
│       ├── close(): Promise<void>  // Closes the browser.
│       ├── createIncognitoBrowserContext(): Promise<BrowserContext>  // Creates an incognito context.
│       ├── defaultBrowserContext(): BrowserContext  // Access to the default browser context.
│       ├── disconnect(): void  // Disconnects Puppeteer from the browser.
│       ├── newPage(): Promise<Page>  // Opens a new page.
│       ├── pages(): Promise<Page[]>  // Lists all open pages in the browser.
│       ├── version(): Promise<string>  // Gets browser version.
│       ├── newTab(): Promise<Page>  // Opens a new browser tab.
│       ├── browserContexts(): BrowserContext[]  // Lists all browser contexts.
│       ├── isConnected(): boolean  // Checks if the browser is connected.
│       └── createBrowserFetcher(options: { host?: string; path?: string }): BrowserFetcher  // Creates a BrowserFetcher instance.
│
├── BrowserContext
│   ├── Properties
│   │   ├── isIncognito(): boolean  // Checks if the context is incognito.
│   │   ├── targets(): Target[]  // Lists all targets in this context.
│   │   ├── pages(): Promise<Page[]>  // Retrieves all pages in this context.
│   │   ├── serviceWorkers(): ServiceWorker[]  // Lists all service workers in the context.
│   └── Methods
│       ├── close(): Promise<void>  // Closes the browser context.
│       ├── overridePermissions(origin: string, permissions: string[]): Promise<void>  // Overrides permissions for a page.
│       ├── resetPermissions(): Promise<void>  // Resets all permission overrides.
│       ├── clearCookies(): Promise<void>  // Clears cookies for the context.
│       ├── cookies(...urls: string[]): Promise<Cookie[]>  // Returns cookies for the specified URLs.
│       ├── setCookie(...cookies: Cookie[]): Promise<void>  // Sets cookies in the context.
│       ├── waitForTarget(predicate: (target: Target) => boolean, options?: { timeout?: number }): Promise<Target>  // Waits for a target to match a condition.
│       └── createCDPSession(): Promise<CDPSession>  // Creates a new Chrome DevTools Protocol session.
│
├── Page
│   ├── Properties
│   │   ├── url(): string  // Returns the page's URL.
│   │   ├── title(): Promise<string>  // Returns the page's title.
│   │   ├── isClosed(): boolean  // Checks if the page is closed.
│   │   ├── frames(): Frame[]  // Lists all frames on the page.
│   │   ├── mainFrame(): Frame  // Returns the main frame of the page.
│   │   ├── viewport(): Viewport | null  // Gets the page's viewport size.
│   │   ├── keyboard: Keyboard  // Keyboard input handler.
│   │   ├── mouse: Mouse  // Mouse input handler.
│   │   ├── context(): BrowserContext  // Returns the browser context of the page.
│   │   ├── metrics(): Promise<Metrics>  // Retrieves performance metrics for the page.
│   │   ├── accessibility(): Accessibility  // Access to accessibility features.
│   │   ├── touchScreen: Touchscreen  // Touchscreen input handler.
│   │   ├── workers(): Worker[]  // Retrieves all workers for the page.
│   │   ├── pdf(options?: PDFOptions): Promise<Buffer>  // Generates a PDF of the page.
│   └── Methods
│       ├── close(): Promise<void>  // Closes the page.
│       ├── goto(url: string, options?: GotoOptions): Promise<Response | null>  // Navigates to a URL.
│       ├── reload(options?: ReloadOptions): Promise<Response | null>  // Reloads the page.
│       ├── screenshot(options?: ScreenshotOptions): Promise<Buffer | void>  // Takes a screenshot.
│       ├── evaluate<T>(pageFunction: Function | string, ...args: any[]): Promise<T>  // Evaluates a function in the page context.
│       ├── type(selector: string, text: string, options?: TypeOptions): Promise<void>  // Types text into an element.
│       ├── click(selector: string, options?: ClickOptions): Promise<void>  // Clicks an element.
│       ├── waitForSelector(selector: string, options?: WaitForSelectorOptions): Promise<ElementHandle | null>  // Waits for a selector to appear.
│       ├── waitForTimeout(milliseconds: number): Promise<void>  // Waits for the specified time.
│       ├── setContent(html: string, options?: SetContentOptions): Promise<void>  // Sets the page content.
│       ├── addScriptTag(options: AddTagOptions): Promise<ElementHandle | null>  // Adds a script tag to the page.
│       ├── addStyleTag(options: AddTagOptions): Promise<ElementHandle | null>  // Adds a style tag to the page.
│       ├── setViewport(viewport: Viewport): Promise<void>  // Sets the page's viewport.
│       ├── bringToFront(): Promise<void>  // Brings the page to the front.
│       ├── waitForNavigation(options?: WaitForNavigationOptions): Promise<Response | null>  // Waits for navigation.
│       ├── $(selector: string): Promise<ElementHandle | null>  // Queries a single element.
│       ├── $$(selector: string): Promise<ElementHandle[]>  // Queries multiple elements.
│       ├── focus(selector: string): Promise<void>  // Focuses an element.
│       ├── waitForNetworkIdle(options?: WaitForNetworkIdleOptions): Promise<void>  // Waits for network to be idle.
│       ├── waitForRequest(urlOrPredicate: string | ((req: Request) => boolean), options?: WaitForRequestOptions): Promise<Request>  // Waits for a request.
│       ├── waitForResponse(urlOrPredicate: string | ((res: Response) => boolean), options?: WaitForResponseOptions): Promise<Response>  // Waits for a response.
│       ├── on(eventName: string, handler: Function): this  // Listens to an event on the page.
│       ├── off(eventName: string, handler: Function): this  // Removes an event listener.
│       ├── evaluateHandle<T>(pageFunction: Function | string, ...args: any[]): Promise<JSHandle<T>>  // Returns a JSHandle.
│       ├── exposeFunction(name: string, pptrFunction: Function): Promise<void>  // Exposes a function to the page's context.
│       └── setGeolocation(options: { latitude: number; longitude: number; accuracy?: number }): Promise<void>  // Sets geolocation for the page.
│
├── Frame
│   ├── Properties
│   │   ├── url(): string  // Returns the frame's URL.
│   │   ├── name(): string  // Returns the frame's name.
│   │   ├── content(): Promise<string>  // Retrieves the frame's content.
│   │   ├── title(): Promise<string>  // Returns the frame's title.
│   └── Methods
│       ├── evaluate<T>(pageFunction: Function | string, ...args: any[]): Promise<T>  // Evaluates a function in the frame.
│       ├── goto(url: string, options?: GotoOptions): Promise<Response | null>  // Navigates to a URL in the frame.
│       ├── waitForSelector(selector: string, options?: WaitForSelectorOptions): Promise<ElementHandle | null>  // Waits for a selector in the frame.
│       └── waitForTimeout(milliseconds: number): Promise<void>  // Waits in the frame for the specified time.
│
├── ElementHandle
│   ├── Methods
│   │   ├── click(options?: ClickOptions): Promise<void>  // Clicks the element.
│   │   ├── hover(): Promise<void>  // Hovers over the element.
│   │   ├── focus(): Promise<void>  // Focuses the element.
│   │   ├── screenshot(options?: ScreenshotOptions): Promise<Buffer>  // Takes a screenshot of the element.
│   │   ├── type(text: string, options?: TypeOptions): Promise<void>  // Types text into the element.
│   │   ├── evaluate<T>(pageFunction: Function | string, ...args: any[]): Promise<T>  // Evaluates a function on the element.
│   │   └── boundingBox(): Promise<BoundingBox | null>  // Gets the element's bounding box.
│
└── PuppeteerErrors
    ├── TimeoutError: Thrown when a timeout occurs during a Puppeteer operation.
    ├── NavigationError: Thrown when a navigation fails.
    └── ProtocolError: Thrown for protocol errors during communication with the browser.

Puppeteer
│
├── Target
│   ├── Properties
│   │   ├── type(): string  // Returns the target's type (e.g., "page", "service_worker").
│   │   ├── url(): string  // Returns the target's URL.
│   │   ├── browser(): Browser  // Returns the browser the target belongs to.
│   │   ├── browserContext(): BrowserContext  // Returns the browser context the target is attached to.
│   │   ├── opener(): Target | null  // Returns the target that opened this target, if any.
│   └── Methods
│       ├── page(): Promise<Page | null>  // Gets the page associated with the target, if any.
│       ├── worker(): Promise<Worker | null>  // Gets the worker associated with the target, if any.
│       ├── createCDPSession(): Promise<CDPSession>  // Creates a new Chrome DevTools Protocol session for the target.
│       ├── isInitialized(): Promise<boolean>  // Checks if the target is initialized.
│       ├── close(): Promise<void>  // Closes the target (only for certain types like "page").
│       └── targetInfo(): TargetInfo  // Returns the target's detailed information.
│
├── Worker
│   ├── Properties
│   │   ├── url(): string  // Returns the worker's URL.
│   │   ├── executionContext(): ExecutionContext  // Returns the execution context of the worker.
│   └── Methods
│       ├── evaluate<T>(pageFunction: Function | string, ...args: any[]): Promise<T>  // Evaluates a function within the worker.
│       ├── evaluateHandle<T>(pageFunction: Function | string, ...args: any[]): Promise<JSHandle<T>>  // Evaluates a function and returns a handle to the result.
│       ├── on(eventName: string, handler: Function): this  // Attaches an event handler for the worker.
│       ├── off(eventName: string, handler: Function): this  // Detaches an event handler for the worker.
│       └── destroy(): void  // Destroys the worker.



```
