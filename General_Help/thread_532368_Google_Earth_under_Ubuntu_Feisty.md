---
title: "Google Earth under Ubuntu Feisty"
date: 2007-08-22
forum: General Help
---

### Post by catgate on 2007-08-22
Some time ago I was informed by someone (don't remember who) that Google Earth would not run under Linux, and yet I now see that Google are offering it as a suitable subject for Linux users,
Can anyone enlighten me on this please?

---

### Post by cookies on 2007-08-22
> **catgate said:**
> Some time ago I was informed by someone (don't remember who) that Google Earth would not run under Linux, and yet I now see that Google are offering it as a suitable subject for Linux users,
Can anyone enlighten me on this please?


Ir runs, and you have to add the MediaBuntu repositories and then do sudo apt-get install googleearth 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by _simon_ on 2007-08-22
Not sure how new it would be in that repo?

You can get it direct from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Then open terminal and install like this:

```

sh GoogleEarthLinux.bin

```

---

### Post by wconstantine on 2007-08-22
My Google Earth crashes at the splash screen. Someone know how to fix this?

---

### Post by _simon_ on 2007-08-22
> **wconstantine said:**
> My Google Earth crashes at the splash screen. Someone know how to fix this?

Using 3D enabled video drivers?

---

### Post by wconstantine on 2007-08-22
> **_simon_ said:**
> Using 3D enabled video drivers?

Yeah.

---

### Post by _simon_ on 2007-08-22
> **wconstantine said:**
> Yeah.

What happens if you run it from terminal?

---

### Post by wconstantine on 2007-08-22
Same thing.

---

### Post by _simon_ on 2007-08-22
no error messages?

---

### Post by wconstantine on 2007-08-22
viljam@snelhest:~$ googleearth 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

That's all but I see that alot of times when running apps from the terminal. Do you reckon I should install xfree86-driver-fglrx?

Edit: I see that I shouldn't install it now...

Edit2: [http://ubuntuforums.org/showthread.php?t=520952&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=520952&highlight=google+earth)
Fixed it.

---

### Post by catgate on 2007-08-23
Thanks I shall try it out.
 Listen for a scream emanating from somewhere near York.

---

### Post by Wroger Wroger on 2007-08-24
> **_simon_ said:**
> Not sure how new it would be in that repo?

You can get it direct from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Then open terminal and install like this:

```

sh GoogleEarthLinux.bin

```


I don't actually hate you, but I hate the poor quality or incomplete information that you have taken it upon yourself to provide.

Here is the MISSING essential bits from the google website:

[http://earth.google.com/support/bin/answer.py?answer=44713&useful=1&show_useful=1](http://earth.google.com/support/bin/answer.py?answer=44713&useful=1&show_useful=1)


How do I install Google Earth on Linux machines?

You can download and install Google Earth for Linux by following these instructions:

1. Visit [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

2. Click on the "Linux" radio button under the category Beta (Version 4), and select "Download Google Earth."

3. "Open a terminal window/console" ---    +   ---- "and navigate to your default downloads directory."------ 

Enter the following command in the directory: > sh GoogleEarthLinux.bin

4. Follow the prompts to complete the installation. The default location for the program is "/usr/local/google/google-earth." 

If Google Earth was installed in its default location, you can launch it using the following command: > /usr/local/google/google-earth/googleearth

---

### Post by dseybert on 2007-08-24
Next time I'll read the whole thread before I post...

---

### Post by tineeshmichael on 2007-08-24
Great post

---

### Post by mhenriday on 2007-08-24
More a **Google Earth** query than an **Ubuntu** one, but after proceeding to the **Google Earth** download page, downloading the **bin** file, and opening it with the shell command «**sh GoogleEarthLinux.bin**» in a terminal, I found to my great surprise (I've never encountered this problem in **Windows** versions) that only **ASCII** characters are accepted in addresses, etc, under «**My places**». Thus, when I attempted to type in my street address, the letter «ä» in «Stadshagsvägen» was distorted to illegibility. I've been unable to find any method to correct this in the tools provided in **Google Earth 4.2** ; if, however, any forum readers know of a way to work 'round this limitation, I'd be most grateful for the information....

Henri

PS : I've tried modifying the languages setting in **Google Earth** via **Tools** &#8594; **Options**, clicking the «**General**» tab, and then proceeding to the **Language Settings** box. Swedish, alas, is not supported, but I tried clicking German, which also uses non-**ASCII** characters, but even with this setting, I was still unable to type in «ä»....

---

### Post by catgate on 2007-08-25
It looks to me in my ignorance to need a better graphics set up than the standard onboard stuff.
When I try to run GE I get the opening screen (dimly) and then I am thrown out and have to reboot.
Beam my up Scotty.

---

### Post by The Pinny Parlour on 2007-08-26
> **_simon_ said:**
> Not sure how new it would be in that repo?

You can get it direct from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Then open terminal and install like this:

```

sh GoogleEarthLinux.bin

```

Awesome.  Many thanks.  An easy and simple way to install.

---

### Post by lammergeir on 2007-09-01
Hi , I tried to install GoogleEarth: sh GoogleEarthLinux.bin
I get: Verifying archive integrity.... Error in MD5 checksums: 3934729ed47565a283701c40eca23c61 is different from 8cf976cf5f8dae0780f87e32f7d7cba
Grateful for any help for this newbie.

---

### Post by OsakaWilson on 2007-09-02
I tried installing, but I get the following. Any idea what is wrong?

XXXXX:~/Desktop$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.180.1134..............................................................

(setup.gtk2:22618): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)
wilson@wilson-desktop:~/Desktop$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.180.1134..............................................................

(setup.gtk2:22618): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)

---

### Post by willz06jw on 2007-09-12
I get the Error in MD5 checksums also...   I have a later version already installed, but I can't get the 4.2 version to even start the upgrade script.

Will:confused:

---

### Post by wammin on 2007-09-12
> Error in MD5 checksums: 3934729ed47565a283701c40eca23c61 is different from 8cf976cf5f8dae0780f87e32f7d7cba

Same problem here. This is a new install on this machine. I think there must be a problem with the dowload file from Google.

---

### Post by stchman on 2007-09-12
> **catgate said:**
> Some time ago I was informed by someone (don't remember who) that Google Earth would not run under Linux, and yet I now see that Google are offering it as a suitable subject for Linux users,
Can anyone enlighten me on this please?

Google Earth runs fine under Linux.  Go to earth.google.com and download the Linux installer.

When you get the installer .bin file type the following:

sudo sh ./GoogleEarthLinux.bin

This will install it in the /opt/GoogleEarth folder.

You will need an openGL driver for your video card and an internet connection to run Google Earth properly.

You can also get GE from Medibuntu as well.

---

### Post by macabro22 on 2007-09-12
Same O

```
Error in MD5 checksums:
```

What to do?

I want Google Sky functionality!

---

### Post by highlighter on 2007-09-12
Same here...Error in MD5 Checksums

---

### Post by mindtrick on 2007-09-12
Downloaded it twice today and I'm getting the md5 error again. I'm gonna contact Google about it.

---

### Post by mindtrick on 2007-09-13
Looks like it's solved. Re-downloaded the binary and installs without any problem.

---

### Post by catgate on 2007-10-06
This has been a very interesting and educational topic (well it's taught me a lesson). 
I gave up to it in March. It looks as though I need a video card and just for Google Earth I could not be arsed (as they say in certain quarters), I seem to have managed for quite a long time with the onboard video package.

---

### Post by vmsda on 2007-10-07
> **_simon_ said:**
> What happens if you run it from terminal?

I downloaded directly from Google, but wherever I run it from, X goes down, then up, since I get the login screen all over again.

By the way, I did not install any of Medibuntu; scanned it, and it says that to have googleearth I have to download the non-free packages. Does that mean that under Medibuntu we have to pay for googleearth?

Thanks for your help

---

### Post by forestpixie on 2007-10-07
no it doesn't mean that you have to pay - it's to do with it not being opensource software

it works fine through the medibuntu repos - I certainly don't have any problems with it at all

---

### Post by Borg on 2007-10-08
All I get is 

>  sudo sh ./GoogleEarthLinux.bin
sh: Can't open ./GoogleEarthLinux.bin


---

### Post by thehagman on 2007-10-13
> **vmsda said:**
> I downloaded directly from Google, but wherever I run it from, X goes down, then up, since I get the login screen all over again.

By the way, I did not install any of Medibuntu; scanned it, and it says that to have googleearth I have to download the non-free packages. Does that mean that under Medibuntu we have to pay for googleearth?

Thanks for your help

Same here: X restarts after the first splash.:(
Google-earth worked ok when I had dapper running (with the version downloaded from Google). After I made the two upgrades to feisty, the installed version did not work any more.
I replaced it with the medibuntu version, but that made no difference (except that the logo ball got  a different shade of blue).

Thanks for any ideas.

---

### Post by thehagman on 2007-10-13
OK, it looks like I finally resolved the issue here (and actually I just notice that I've accidentally landed in a ubuntuforum, not kubuntu, but anyway)

First,
 [INDENT]$ lspci | grep VGA 
 01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)[/INDENT]
so I try
 [INDENT]sudo apt-get install nvidia-glx[/INDENT]
Result (without reboot): google-earth (kind of) works but frames are built slowly one by one
Reboot.
Result: image is black - no earth, no stars.
 [INDENT]sudo nvidia-glx-config enable[/INDENT]
and shoulder-shruggingly confirm a warning message.
Reboot.
Result: X won't start
A diff of /etc/X11/xorg.conf and /etc/X11/xorg.conf.<timestamp> shows that (among others) the wrong PCI id occurs.
 [INDENT]sudo vi /etc/X11/xorg.conf[/INDENT]
to replace "0:5:0" with "1:0:0" (cf. lspci).
 [INDENT]startx[/INDENT]
Result: google-earth starts and runs smoooothly :guitar:
However, other unrelated problems in xorg.conf still needed to be resolved (by comparing with the older version): I suddenly had a 104 key us keyboard instead of 105 key de nodeadkeys. And the display resolution....
:popcorn:

---

