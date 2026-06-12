---
title: "How to start Libreoffice Draw to fill in .pdf form"
date: 2024-03-14
forum: General Help
---

### Post by satimis on 2024-03-14
Hi

I need to fill in .pdf form but unable to start LibreOffice Draw

LibreOffice```

Version: 7.6.5.2(X86_64)
Ubuntu package version:
4:7.6.5-Oubuntu0.23.14.1_bpo22.04.1

```

$ apt policy libreoffice-impress```

libreoffice-impress:
  Installed: 4:7.6.5-0ubuntu0.23.10.1~bpo22.04.1
  Candidate: 4:7.6.5-0ubuntu0.23.10.1~bpo22.04.1
  Version table:
 *** 4:7.6.5-0ubuntu0.23.10.1~bpo22.04.1 100
        100 http://hk.archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.3.7-0ubuntu0.22.04.4 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     1:7.3.2-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

Impress already installed.

Please advise.  Alternatively is there a better solution filling in .pdf form and to sign it?

Thanks in advance.

Regards

---

### Post by 14nd on 2024-03-14
i used to use foxit pdf when i was on windows ,which one can fill and sign.
am yet to try to install it in linux ...

---

### Post by HermanAB on 2024-03-14
I prefer to use xournal. It creates an overlay. When done editing, do  Export to PDF for the final.

---

### Post by dragonfly41 on 2024-03-14
I have Master PDF Editor in my toolset. But there is a price attached.

P.S. Demo version (with watermark) here ..

[https://code-industry.net/get-masterpdfeditor/](https://code-industry.net/get-masterpdfeditor/)

---

### Post by VMC on 2024-03-14
I also prefer "**xournal**" as Herman stated.

---

### Post by satimis on 2024-03-14
Hi@HermanAB and VMC

Thanks for your advice

"xournal" is on repo

$ apt policy xournal```

xournal:
  Installed: (none)
  Candidate: 1:0.4.8.2016-7build1
  Version table:
     1:0.4.8.2016-7build1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

xournal can also be installed via snap or flatpak

Which installation method shall I use?

Besides can I sign the pdf form with hand writing?

Thanks

Regards

---

### Post by VMC on 2024-03-14
xournal stop development in 2016. xournal++ is suppose to be its replacement.
Here's a comparision to see the difference:
[https://github.com/xournalpp/xournalpp.github.io/pull/23/files](https://github.com/xournalpp/xournalpp.github.io/pull/23/files)
I don't use Snap or flatpak. So can't advise on that.

---

### Post by #&amp;thj^% on 2024-03-14
> **satimis said:**
> 
Which installation method shall I use?

Besides can I sign the pdf form with hand writing?

Thanks

Regards

I do flatpaks, and here is a sample to your question.
This is the flatpak version used.
```
 1) app/net.sourceforge.xournal/x86_64/stable
   2) app/com.github.xournalpp.xournalpp/x86_64/stable

Which do you want to use (0 to abort)? [0-2]: 2

com.github.xournalpp.xournalpp permissions:
    ipc       fallback-x11          pulseaudio            wayland
    x11       file access [1]       dbus access [2]

    [1] host, xdg-run/dconf, xdg-run/gvfs, xdg-run/gvfsd, xdg-run/pipewire-0,
        ~/.config/dconf:ro
    [2] ca.desrt.dconf, org.gtk.vfs.*


        ID                                    Branch Op Remote  Download
 1. [&#10003;] com.github.xournalpp.xournalpp.Locale stable i  flathub  7.4*kB / 1.3*MB
 2. [&#10003;] com.github.xournalpp.xournalpp        stable i  flathub 99.7*MB / 112.5*MB


```

---

### Post by monkeybrain20122 on 2024-03-14
qpdfview can fill standard pdf forms [https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb](https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb)

Besides, it is the best pdf viewer on Linux, it is lightweight, very fast and featureful, It is the only pdf reader on Linux that supports tabs and does it well. Okular says it does but kind of glitchy and very resource hungry and last time I checked about a year ago it couldn't remember opened tabs after restarting the app. Foxit Linux  support tabs but only 20 of them, with qpdfview you can easily open 50-60 with no issue. Unlike the Windows version Foxit Linux has very few features, it can't open djvu files (all Linux pdf viewers can), it is closed source and TBH I don't even know if its development has ceased. It doesn't completely shutdown unless you start it in the terminal, otherwise it lurks behind and eats all your memory after you think you have closed it, this is an old bug that has been reported years ago, it was not fixed as of last year when I was just curious and wanted to see what it could do.

I think qpdfview definitely deserve more attentions. Definitely the best. Much better than Evince and Okular.

---

### Post by satimis on 2024-03-15
> **VMC said:**
> xournal stop development in 2016. xournal++ is suppose to be its replacement.
Here's a comparision to see the difference:
[https://github.com/xournalpp/xournalpp.github.io/pull/23/files](https://github.com/xournalpp/xournalpp.github.io/pull/23/files)
I don't use Snap or flatpak. So can't advise on that.
Hi@VMC

Thanks for your advice

xournal++ is on daily build.  Then I must update it each day?

Regards

---

### Post by 14nd on 2024-03-15
following this as i'm in the market for a proper PDF suite 
ima give this a try 
already installed Okular and briefly checked it out and already didn't like it , removing it .
installed foxit too cause it was great on windows but as u said many futures   not there on linux version . removing that  too.
next up ima give this qpdfview a go ...

thanks !  :)

ps: looked at xournal ++ too , but it doesn't look like a proper pdf thing looks more like a note/sketchpad deal ? maybe i'm wrong

---

### Post by VMC on 2024-03-15
I installed the newer xournalpp. It does have some improvements.

---

### Post by Holger_Gehrke on 2024-03-15
@satimis: the daily builds are (more or less) for debugging. There are releases which you should use in production.

@14nd: Yes, xournal(++) is a note-taking application. It does have a function 'Annotate PDF' in the file-menu, which makes it possible to fill out forms that are meant to be printed and filled out by hand (still quite common in German bureaucracy ...). This function probably started live as a tool for 'active reading' - putting your comments and questions into the text while you're reading it. You basically get the PDF as a background layer for your notes and when you export the whole thing as a pdf again you have a PDF of the filled out form ...

Holger

---

### Post by TheFu on 2024-03-15
> **HermanAB said:**
> I prefer to use xournal. It creates an overlay. When done editing, do  Export to PDF for the final.

+1.

---

### Post by satimis on 2024-03-15
> **TheFu said:**
> +1.
Hi@TheFu,

Now I'm a little bid confused.  Which version of xournal shall I install for testing

On Ubuntu repo
or
Snap
or
Flatpak
or
xournal(++) 

If xournal(++)  which version shall I install?  Not the daily build version

Regards

---

### Post by 14nd on 2024-03-15
update : tried qpdfview (preinstalled with MX) , and found not what i'm looking for .
then tried xournal and so far works perfect :)

installed it with```
sudo apt install xournal
```

---

### Post by Paulgirardin on 2024-03-22
I need to fill many different PDF forms and generally use Firefox for interactive forms , it has a very good PDF viewer with tabs. In my opinion it is better than Foxit or Okular.
Every time I try Okular it is a disaster.
I use Xournal++ to fill noninteractive forms.
And Sioyek for reading PDF service manuals.

---

### Post by Paulgirardin on 2024-03-22
> **14nd said:**
> update : tried qpdfview (preinstalled with MX) , and found not what i'm looking for .
then tried xournal and so far works perfect :)

installed it with```
sudo apt install xournal
```

					Be aware that the Ubuntu repos have both xournal and xournal++
If you used the command:
 	Code:
 	```
sudo apt install xournal
``` 
You did not install the version that is fully current (xournal++) and is actively under development

---

### Post by 14nd on 2024-03-25
noted , thanks for that 
is there a simple command like above one that installs it?
i get unable to locate package

---

### Post by 14nd on 2024-03-25
nevermind ,found it
```
[COLOR=#36464E][FONT=&quot]sudo apt install xournalpp[/FONT][/COLOR]
```

now got xournal++ , so worked for me 

thanks !

---

