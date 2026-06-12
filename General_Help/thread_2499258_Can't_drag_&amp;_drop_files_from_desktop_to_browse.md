---
title: "Can't drag &amp; drop files from desktop to browser (i.e. Google Drive)"
date: 2024-07-20
forum: General Help
---

### Post by Brent_Santin on 2024-07-20
Hi, I'm using Lubuntu 20.04.6.

Recently (like in the past month) I've notice that I can no longer drag files from the desktop into my browser. When I do so, the mouse pointer just shows a red "NO" symbol (red circle with diagonal line through it).
This happens when I try to drag and drop a file into Google Drive, MicroSoft OneDrive, or attach files to a web-based e-mail I'm composing (i.e. G-mail, Yahoo mail).

I'm not sure what "broke" this functionality.

I've tried clearing my browser cache and rebooting.  I've tried Incognito mode (private browsing mode) with no luck.

My web-browser is Firefox.

Does anyone have a clue what is preventing this from working?

Thanks.

---

### Post by TheFu on 2024-07-21
Is firefox a snap package on your system?  If so, it runs with forced constraints and only specifically allowed programs are allowed to interface with it.  In the snap world, they call them "connections".  

That's my guess, but I don't **know** that's the issue.  I don't work in that way.

Years ago, most of the major browsers decided that we shouldn't be allowed to open HTML files stored on our desktops. They said it was a security feature to prevent some nasty things, which is probably true.  This was before Canoncial decided to start pushing snap packages.

I don't use Lubuntu and I don't know which firefox it has on 20.04.  I do run 20.04, but I use Firefox-ESR which comes from a mozilla PPA. This is my way to avoid snaps.  Some of my workflows require a few different programs to work together that the snap people never considered.  After all, if we wanted to be forced to work in only 1 way, then we'd run MacOS, right?

If you don't have a snap version of firefox installed, then it can't be the snap constraints. It might be a default setting that you'll need to find inside about:config.  Google found this: [https://kb.mozillazine.org/Links_to_local_pages_do_not_work](https://kb.mozillazine.org/Links_to_local_pages_do_not_work)

---

### Post by Brent_Santin on 2024-07-29
Okay...I checked and it doesn't appear that my Installation of FireFox is a snap package.

Furthermore, I installed the Chromium web browser, to see if it would have the same problem.  The only version available to me was in a Snap package, so I installed it.
Chromium (Snap) does work fine with drag and drop from desktop into browser (tested in Google Drive).  

So this appears to be a problem with Firefox, but as I said it only appeared in the past month.  I'm not sure what changed!

Does anyone have an idea?

Thanks.

---

### Post by Brent_Santin on 2024-07-30
Update:

I tried:

- Completely uninstalling FireFox, including preferences folder. 
- Tried reinstalling via the snap package, and also the non-snap way.  
- Tried starting Firefox in Troubleshooting (i.e. safe) mode.

Nothing fixed the issue.

Chromium installed as a Snap package, however, continues to work fine fro drag & drop.

Brent

---

### Post by currentshaft on 2024-07-30
What happens if you try opening the file in Firefox - put "file:///home/" in the address bar and find it.

---

### Post by Brent_Santin on 2024-07-30
> **currentshaft said:**
> What happens if you try opening the file in Firefox - put "file:///home/" in the address bar and find it.

That method works. i.e. If I right click a pdf on my desktop and choose "open with Firefox" it loads up in Firefox.
However, when I try and drag the pdf from my desktop into the Firefox window I get the red circle with a slash through beside my mouse pointer.

Unfortunately, for online services like Google Drive, the only way to upload files is to drag them from the desktop into the browser.

---

### Post by currentshaft on 2024-07-31
Can you open about:support in Firefox and see what it says under Window Protocol?

---

### Post by Norm24 on 2024-07-31
I'm running FF installed through Ubuntuzilla ppa and have no issues dragging and dropping files into the browser.I'm using Ubuntu Mate 22.04 but that shouldn't make a difference when it comes to that particular function.

---

### Post by #&amp;thj^% on 2024-07-31
Is any sand-boxing tools in play here? (firejail is one)

Something like this will show us what you have now:
```
apt policy firefox
firefox:
  Installed: 128.0.3~build1
  Candidate: 128.0.3~build1
  Version table:
     1:1snap1-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
 *** 128.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by &amp;KyT$0P# on 2024-07-31
> **Brent_Santin said:**
> Okay...I checked and it doesn't appear that my Installation of FireFox is a snap package.

What type of installation is it (deb from Mozilla, deb from mozillateam PPA, tarball downloaded from Mozilla, flatpak,...)?

> **Brent_Santin said:**
> If I right click a pdf on my desktop and choose "open with Firefox" it loads up in Firefox.

That is not the same as going to [FONT=monospace]file:///home/[/FONT] in Firefox and clicking within Firefox from there to locate and open the file.

If you've opened the file with right-click > "Open with Firefox" in the current browser session, completely quit Firefox and start it new (not opening the file) before trying this troubleshooting test.

---

### Post by antoine132 on 2024-08-02
I have the same problem, also on Lubuntu. This problem appeared somewhat recently.
 I have tried updating Firefox to the latest version, and also with a freshly installed Firefox-ESR (latest version), both from Mozilla's repository. This did not solve the problem.
Also, drag and dropping files works just fine on Chrome on the same machine.

> **currentshaft said:**
> What happens if you try opening the file in Firefox - put "file:///home/" in the address bar and find it.

It works for me, opens the file in browser as usual. 

> **halogen2 said:**
> What type of installation is it (deb from Mozilla, deb from mozillateam PPA, tarball downloaded from Mozilla, flatpak,...)?

My original install was .deb through ubuntu repositories, then from Mozilla's repository. Neither worked.

> **1fallen said:**
> Is any sand-boxing tools in play here? (firejail is one)

Something like this will show us what you have now:
```
apt policy firefox
firefox:
  Installed: 128.0.3~build1
  Candidate: 128.0.3~build1
  Version table:
     1:1snap1-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
 *** 128.0.3~build1 1000
       1000 https://packages.mozilla.org/apt mozilla/main amd64 Packages
        100 /var/lib/dpkg/status

```

This is what I get:
```
firefox:
  Installed: 128.0.3~build1
  Candidate: 128.0.3~build1
  Version table:
 *** 128.0.3~build1 500
        500 https://packages.mozilla.org/apt mozilla/main amd64 Packages
        100 /var/lib/dpkg/status
     128.0.2~build1 500
        500 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     128.0+build2-0ubuntu0.20.04.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     128.0~build2 500
        500 https://packages.mozilla.org/apt mozilla/main amd64 Packages
     127.0.2~build1 500
        500 https://packages.mozilla.org/apt mozilla/main amd64 Packages
(plus many more previous versions)
```

Hope this can help.

BTW,
> **Brent_Santin said:**
> That method works. i.e. If I right click a  pdf on my desktop and choose "open with Firefox" it loads up in Firefox.
However, when I try and drag the pdf from my desktop into the Firefox  window I get the red circle with a slash through beside my mouse  pointer.

Unfortunately, for online services like Google Drive, the only way to  upload files is to drag them from the desktop into the browser.

You can add a file to Google Drive by sending it to the associated Gmail address (if you have one), and then clicking the "add to Drive" icon on attached file in the email.

---

### Post by #&amp;thj^% on 2024-08-02
I sandbox mine with firejail, and from my /Documents to drag goes like:
```

File not found

Firefox can’t find the file at /home/me/Documents/A Beginner's Guide to Editing Text Files With Vi.pdf.

    Check the file name for capitalization or other typing errors.
    Check to see if the file was moved, renamed or deleted.
```
Now if I copy that file to Downloads i get this, See screenshot.

---

### Post by antoine132 on 2024-08-05
(Not OP, see my previous post)

> **currentshaft said:**
> Can you open about:support in Firefox and see what it says under Window Protocol?
It's x11 for me

---

### Post by antoine132 on 2024-08-06
Here's another behaviour I observed:

I can switch focus from PCManFM to Firefox (FF) while dragging a file. I know that because I can navigate the toolbar bookmarks with the file as if it was a bookmark (while the cursor looks like this [IMG]https://i.imgur.com/O7A6dUJ.png[/IMG][IMG]https://imgur.com/O7A6dUJ[/IMG][IMG]https://imgur.com/a/wNmY7Fv[/IMG][IMG]https://imgur.com/O7A6dUJ[/IMG]). This is expected behaviour because you can  do this with local files to bookmark them in FF. However, currently, I can only *drag* the file in the toolbar bookmarks; *dropping* it does nothing. It does not create a bookmark associated with the local file path as it should.

This is the only way I found to switch focus from PCManFM to FF while dragging a file. Dragging it to the address bar or  on the web page is almost always met with this symbol : [IMG]https://i.imgur.com/NmKb0Bq.png[/IMG].

Turns out, while making this post, I observed that Imgur image uploader recognized I was trying to drop a file. It did not work, but it's the first time I've seen a web page exhibit this behaviour since my problem started.

---

### Post by antoine132 on 2024-08-27
Welp, it seems it's a File Manager issue. My previously mentioned problems occured while using PCManFM, whereas everything works just fine with Caja. 
I hope this can be of any help to anyone in the future.

---

