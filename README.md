# Public Gallery — real multi-user server

This is a real server-backed gallery, not a demo/mockup.

## What it does
- Public URL: anyone visiting the same server URL sees the same files.
- Upload images, videos, and other files from phones, iPads, and desktop browsers.
- Original bytes are stored on the server; the browser does not resize or recompress uploads.
- Real-time updates using Socket.IO: when someone uploads/deletes, connected viewers update.
- Download button serves the original stored file.
- Delete is allowed only from the browser that originally uploaded the file (identified by a local owner token). No email is collected.
- Vertical scrolling; light theme; black text; rounded/capsule cards; large `+` button.

## Run
Requires Node.js 18+.

```bash
npm install
npm start
```

Open: `http://localhost:3000`

## Make it public
Deploy this whole folder to a Node-compatible host with persistent disk/storage. The same URL is then shared with everyone. Do not use an ephemeral filesystem if you need uploaded files to survive restarts/redeploys.

## Storage
There is no application-level per-file size setting in this version. Practical limits come from the hosting provider, disk space, reverse proxy, and network. "Unlimited" therefore means the app itself does not impose a normal small gallery quota; storage is still physically finite.

## Important production note
The delete protection uses a browser-local owner token, not an account/login. Clearing browser storage or moving to another device will remove the ability to delete a file from that browser. For stronger ownership control, add authentication.
