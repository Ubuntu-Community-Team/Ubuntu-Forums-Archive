---
title: "npm update error"
date: 2017-09-25
forum: General Help
---

### Post by littlemonkey2 on 2017-09-25
After doing:
git clone [https://github.com/zone117x/node-cryptonote-pool.git](https://github.com/zone117x/node-cryptonote-pool.git) pool
[COLOR=#005CC5]cd[/COLOR] pool
npm update
I get a stack of errors (100+ lines), some of them look like this:
gyp ERR! build error
gyp ERR! stack Error: `make` failed with exit code: 2
gyp ERR! stack     at ChildProcess.onExit (/usr/lib/node_modules/npm/node_modules/node-gyp/lib/build.js:276:23)
gyp ERR! stack     at emitTwo (events.js:106:13)
gyp ERR! stack     at ChildProcess.emit (events.js:191:7)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:219:12)
gyp ERR! System Linux 4.9.33-mod-std-ipv6-64
gyp ERR! command "/usr/bin/node" "/usr/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /home/carlos/pool/node_modules/multi-hashing
gyp ERR! node -v v6.11.3
gyp ERR! node-gyp -v v3.4.0
gyp ERR! not ok
cryptonote-pool@0.0.1 /home/carlos/pool
&#9492;&#9472;&#9472; cryptonote-util@0.0.3  (git://github.com/Snipa22/node-cryptonote-util.git#49d6ec72d499bba9144d4a3ebdf4b62a4262aa8a)


npm ERR! Linux 4.9.33-mod-std-ipv6-64
npm ERR! argv "/usr/bin/node" "/usr/bin/npm" "update"
npm ERR! node v6.11.3
npm ERR! npm  v3.10.10
npm ERR! code ELIFECYCLE


npm ERR! multi-hashing@0.0.9 install: `node-gyp rebuild`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the multi-hashing@0.0.9 install script 'node-gyp rebuild'.
npm ERR! Make sure you have the latest version of node.js and npm installed.
npm ERR! If you do, this is most likely a problem with the multi-hashing package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     node-gyp rebuild
npm ERR! You can get information on how to open an issue for this project with:
npm ERR!     npm bugs multi-hashing
npm ERR! Or if that isn't available, you can get their info via:
npm ERR!     npm owner ls multi-hashing
npm ERR! There is likely additional logging output above.

---

### Post by unequipped on 2017-11-09
> **littlemonkey2 said:**
> After doing:
git clone [https://github.com/zone117x/node-cryptonote-pool.git](https://github.com/zone117x/node-cryptonote-pool.git) pool
[COLOR=#005CC5]cd[/COLOR] pool
npm update
I get a stack of errors (100+ lines), some of them look like this:
gyp ERR! build error
gyp ERR! stack Error: `make` failed with exit code: 2
gyp ERR! stack     at ChildProcess.onExit (/usr/lib/node_modules/npm/node_modules/node-gyp/lib/build.js:276:23)
gyp ERR! stack     at emitTwo (events.js:106:13)
gyp ERR! stack     at ChildProcess.emit (events.js:191:7)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:219:12)
gyp ERR! System Linux 4.9.33-mod-std-ipv6-64
gyp ERR! command "/usr/bin/node" "/usr/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /home/carlos/pool/node_modules/multi-hashing
gyp ERR! node -v v6.11.3
gyp ERR! node-gyp -v v3.4.0
gyp ERR! not ok
cryptonote-pool@0.0.1 /home/carlos/pool
&#9492;&#9472;&#9472; cryptonote-util@0.0.3  (git://github.com/Snipa22/node-cryptonote-util.git#49d6ec72d499bba9144d4a3ebdf4b62a4262aa8a)


npm ERR! Linux 4.9.33-mod-std-ipv6-64
npm ERR! argv "/usr/bin/node" "/usr/bin/npm" "update"
npm ERR! node v6.11.3
npm ERR! npm  v3.10.10
npm ERR! code ELIFECYCLE


npm ERR! multi-hashing@0.0.9 install: `node-gyp rebuild`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the multi-hashing@0.0.9 install script 'node-gyp rebuild'.
npm ERR! Make sure you have the latest version of node.js and npm installed.
npm ERR! If you do, this is most likely a problem with the multi-hashing package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     node-gyp rebuild
npm ERR! You can get information on how to open an issue for this project with:
npm ERR!     npm bugs multi-hashing
npm ERR! Or if that isn't available, you can get their info via:
npm ERR!     npm owner ls multi-hashing
npm ERR! There is likely additional logging output above.


your node version needs to be .10 that is why you are getting this error. I was searching for a different error thats why I am only responding now .

---

