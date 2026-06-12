---
title: "Yuck, ugly fonts"
date: 2008-05-22
forum: General Help
---

### Post by robz0rz on 2008-05-22
I've installed Ubuntu 8.04 (32bits) on my PC last weekend, and I haven't booted back to Windows since. I'm loving the experience.

I've managed to customize the OS to my needs, installing the apps and the tools I like. I'm starting to understand the basics and the power of the terminal.

Somewhere along the road, I installed a package along the lines of 'mstcorefonts' (I believe with wine). This was supposed to give me the nice Windows fonts.

Ever since, in a lot of places, I keep seeing the ugly Arial font back. I was hoping for the Vista fonts (all those fonts that have a name that begins with a C). Instead, I get the ugly old Windows fonts, and to top it all off, they can't be smoothened out!

An example of where I see the fonts back where I don't ant them is Firefox. I managed to get rid of the ugly fonts here by setting in the options that DejaVu is to be used at all times, even if a website uses another font. This doesnt look good on all websites, Id rather have nice smoothed (ClearType?) fonts. Also, I see the font back in the history of Pidgin conversations when they open up.

Is there a way to smoothen out the fonts and to get the nice Vista fonts aswell? The standard options under Appearance->Font don't apply to TrueType fonts it seems...

Thanks for any replies

---

### Post by garyedwardjohnston on 2008-05-22
[http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/](http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/)

[http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html)

---

### Post by mano cazalet on 2008-05-22
Another [link]("https://wiki.ubuntu.com/Fonts"), maybe it will be useful.

And yet [another]("http://ubuntusite.com/fix-get-best-firefox-font-linux/"), if you want to install the Segoe UI fonts to (in this blog look at the section starting with Update)

---

### Post by HousieMousie2 on 2008-05-22
> **robz0rz said:**
> I've installed Ubuntu 8.04 (32bits) on my PC last weekend, and I haven't booted back to Windows since. I'm loving the experience.

~~~~~~~

Is there a way to smoothen out the fonts and to get the nice Vista fonts aswell? The standard options under Appearance->Font don't apply to TrueType fonts it seems...

Thanks for any replies

I don't know about Ubuntu, but in Kubuntu TTF's are supported.
If you have a dual boot, like I do, you can install them out of the Windows Fonts folder.

For me it is System Settings/ Appearance/ Font Installer... Add Fonts... then browse to your Windows Font directory.

Home this helps... seems easier than having to go fetch them off of the web, if you can avoid it.

HousieMousie2

---

### Post by robz0rz on 2008-05-23
Hmm... I am stills truggling with smoothening out the fonts. I can live with setting Firefox to display everything in DejaVu. What I would really like to change though is the standard "sans" and "serif" fonts to be the DejaVu fonts. I hope this will also get rid of ugly fonts on my login screen.

---

### Post by kerry_s on 2008-05-23
run> **sudo dpkg-reconfigure fontconfig-config**

say no to bitmap fonts, reboot and enjoy.

---

### Post by odysseusjak on 2008-05-23
I saved my Windows fonts from my past Windows/Office days.  Whenever I install an OS, I copy that folder to my home directory, then I make it a hidden file (in other words, I save the folder as '.fonts').  When I reboot, all of the fonts are available for the entire OS -- web browsers, office suites, text editors, whatever.

Also, I have a litte '.fonts.conf' file that has the following info in it:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

I copy and paste this file, too.  After I reboot, all my fonts look stunning!

---

