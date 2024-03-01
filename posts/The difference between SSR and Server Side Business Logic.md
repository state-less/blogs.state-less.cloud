React Server is not meant to be a SSR tool. It's a serverside framework. The difference is that React Server facilitates _serverside business logic_, not _serverside rendering_.

## Why is React Server not doing SSR?

Because bundlers like Vite and Next.js already support SSR and we don't want to couple SSR to React Server. We will provide decoupled components that can be used to facilitate SSR (`<ViteDevServer />`, `<ExpressRoute />` and `renderToString`) these need to be used together with the frontend library which will support a `{ssr: boolean}` option which can be used to obtain data for a component during SSR using the same `useComponent` hook as on the client.

## Server

A server is both, a physical computer or a _running process_ which provides one or many services.

A Node.js server would be the running process which provides services like e.g. a REST API / Express server, an Apollo server, a WebPush Notification service or a Game Server, a File Server and whatever you might want to serve.

A SSR service could be one service running on a server.

## Serverside Framework

A serverside framework is a framework that runs on Node.js. Like Express or Apollo. React Server is a serverside framework which can be run on any Node.js server >= v16

## SSR

SSR just renders frontend code to HTML on the server. This usually happens within a HTTP request and provides the HTML for the initial page load.

With Vite and Node.js you would probably use Express to handle SSR. With React Server, the Vite Dev Server and SSR route can be implemented as a microservice / component. e.g. `<SSR route="/" />`

React Server currently supports [SSR by using Next.js](/SSR). There will also follow support for [SSR with Vite](/vite)<sup>1</sup> which is described [here](https://vitejs.dev/guide/ssr).

<sub>1 - once we worked out a generic way to integrate it into the frontend library which keeps SSR logic decoupled from the rest of the React Server framework.</sub>

## Serverside business logic

Serverside business logic is the logic that happens inside of a service / microservice.
e.g. Express routes usually contain business logic like handling authentication, fetching/updating data.

## React Server

React Server is a server that hosts many microservices using declarative components to render these services in a plug and play fashion.

_SSR_ could be one such microservice. The backend logic for the [Forum](https://blogs.state-less.cloud) is another one (`<Forum key="main-forum" />`).

Those components provide the backend logic for these microservices. e.g. authentication, fetching and storing data and functions that change state and operate on data.

## Components

React Server components allow you to write backend logic / microservices as components, using states and hooks to manage lifecycle on the server.

This allows a declarative component based approach of structuring your backend codebase.

React Server components are not meant to be rendered to HTML<sup>2</sup>, they are consumed by a frontend/client and only their data/props will be sent to the client, not pre-rendered HTML.

<sub>2</sub> they might eventually support rendering to web components which contain html with inlined data and javascript to hydrate the html, so that it can be embedded as self contained component
