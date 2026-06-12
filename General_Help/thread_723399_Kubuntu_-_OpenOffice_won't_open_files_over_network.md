---
title: "Kubuntu - OpenOffice won't open files over network."
date: 2008-03-13
forum: General Help
---

### Post by HomerSimpson748 on 2008-03-13
I have an interesting problem that I am hoping someone can shed some light on.

I am trying to open OpenOffice spreadsheets on a co-workers Kubuntu machine. I use konqueror or dolphin to browse to the location of the share, then double click the icon to open the file. The OpenOffice splash screen appears, the progress bar shows that OpenOffice is loading, the splash screen then disappears and calc never opens the file. Manually opening and browsing the share from within calc I can open the file but get the message - Protocal "smb" is supported only partially. Local copy of the file will be created.

So I tried to replicate the problem on my machine with Ubuntu Gutsy. I installed the Kubuntu desktop and have no problem using dolphin or konqueror to browse the shares and open files.

I've ruled out any permissions issues on the server. Can anyone think of where to go next? :confused:

---

### Post by linuxaz on 2008-03-13
Homer,
I don't think this is an Ubuntu bug.  Actually, OpenOffice by default will not open files over a network location.  There is a file you can comment out in the soffice.bin file that will allow this.  I could be wrong, but I'm pretty sure that it.  My default install of SUSE did the same thing on my NFS share until I commented out the line.

Try this.
[http://www.crazysquirrel.com/computing/debian/bugs/openoffice-over-nfs.jspx](http://www.crazysquirrel.com/computing/debian/bugs/openoffice-over-nfs.jspx)

Perhaps there is a better solution.  If so, I'd like to hear about ti too....

bertman

---

### Post by HomerSimpson748 on 2008-03-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/openoffice/+bug/15451](https://bugs.launchpad.net/openoffice/+bug/15451) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well, I don't think this is a locking problem. I'm actually accessing a smb share - not nfs. There has been a rather lengthly discussion at [https://bugs.launchpad.net/openoffice/+bug/15451]("https://bugs.launchpad.net/openoffice/+bug/15451") going back to about 2005.

There was some discussion about it being a OOo kde support problem, but I would think the fact that it works under the Kubuntu desktop running on an Ubuntu install rules that out.

---

### Post by HomerSimpson748 on 2008-03-14
An interesting development...

I installed the ubuntu-desktop on the kubuntu box - and the kubntu-desktop works. I run the kubuntu-desktop and I can browse to network shares using konqueror or dolphin and open OOo files - just the way it should work. So at the very least, we have a workaround.

---

