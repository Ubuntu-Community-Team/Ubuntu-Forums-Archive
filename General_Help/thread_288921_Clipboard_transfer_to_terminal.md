---
title: "Clipboard transfer to terminal?"
date: 2006-10-30
forum: General Help
---

### Post by drfox on 2006-10-30
At my office, I use Terminal Server Client/Remote Desktop to log onto a Windows 2003 Server. Everything works fine except I can't share my clipboard between Ubuntu and Windows.

Is there a way to share the clipboard between Ubuntu and Windows?

Larry

---

### Post by betawind on 2007-10-18
Run rdesktop from a command line (or put it in a shell script and sudo chmod +x <file>) with the "-r clipboard:PRIMARYCLIPBOARD" option.  You will want to configure the plethera of other options as well, but this will get your clipboard working.  Also, I dont know if this makes a difference, but im running rdesktop 1.5.  I did *not* see this option in the tsclient, but it looks like you can run it w/ the -x FILE option to run it with the parameters outlined in FILE.

Hope this helps, 

Beta

---

