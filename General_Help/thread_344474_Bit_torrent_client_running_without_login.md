---
title: "Bit torrent client running without login"
date: 2007-01-23
forum: General Help
---

### Post by nate010111 on 2007-01-23
I'm using a server computer for all my bit torrent downloading and some other functions.  I like to use folder monitoring on the server and remotely drop torrent files that I want downloaded into the server's monitor folder.  My problem is that I'm never logged in to the server and sometimes my server might restart.  In either case I don't want my downloads to stop nor do I want to use auto-login.  I was hoping someone could tell me how to have a program like ktorrent, azureus or utorrent run without logging in(at boot).  If it's not possible to use a gui program then could I use something like rtorrent instead?  How would I later access these programs if there running in the background? Thanks

---

### Post by nate010111 on 2007-01-24
I found the solution to a bit torrent server by adding command line support to Azureus and following this guide:
[http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot](http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot)

My issue is now with the swing web interface used to control Azureus from remote.  When I open the remote web page I get the error in a java applet window: "RequestDispatch fails".  Has anyone seen this error and/or knows how to correct it?

---

### Post by vemon on 2007-12-10
I'm getting the same error in Gutsy and the azureus from ubuntu repositories. If anyone has a fix to this then please share your wisdom :)

---

