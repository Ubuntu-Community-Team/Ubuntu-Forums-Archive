---
title: "Problem installning browser sync"
date: 2019-05-01
forum: General Help
---

### Post by leopardsunset on 2019-05-01
Hi,

I've started a web development course and need to install browser sync. Before that I have installed node and npm. Successfuly I think, since I can do the command node --v and npm --v to get the version-number. 

However, once I try instlall Browser sync I receive the following error message. What am I doing wrong?

npm WARN checkPermissions Missing write access to /usr/lib/node_modules
npm ERR! path /usr/lib/node_modules
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall access
npm ERR! Error: EACCES: permission denied, access '/usr/lib/node_modules'
npm ERR!  { [Error: EACCES: permission denied, access '/usr/lib/node_modules']
npm ERR!   stack:
npm ERR!    'Error: EACCES: permission denied, access \'/usr/lib/node_modules\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/lib/node_modules' }
npm ERR! 
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR! 
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator (though this is not recommended).

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/XXXX/.npm/_logs/2019-05-01T11_51_15_789Z-debug.log

---

### Post by dragonfly41 on 2019-05-01
I have hit permission errors before in writing Electron app and I found this guide to be helpful ..

[https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally#manually-change-npms-default-directory](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally#manually-change-npms-default-directory)

---

