---
title: "Fontconfig warning invalid constant used lcdfilterlegacy"
date: 2008-04-26
forum: General Help
---

### Post by Endolith on 2008-04-26
I found this great program [Sonic Visualiser]("http://www.sonicvisualiser.org/") a while ago, and have been using it.  There's [no package in Ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/196225"), but it's only four files.

But after upgrading to Hardy Heron it shows this error when I try to run it from the command line:

```
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdfilterlegacy
fish: Job 1, “./Programs/sonic-visualiser/sonic-visualiser -v” terminated by signal SIGSEGV (Address boundary error)

```

Does anyone know what this means?  A font configuration has changed and this no longer works with it?

The .conf file it references is just this:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- conf.d/monospace-lcd-filter.conf -->
<fontconfig>
<!--  Use legacy LCD filter on smaller Monospace fonts -->
  <match target="font">
    <test name="family">
      <string>DejaVu Sans Mono</string>
      <string>Bitstream Vera Sans Mono</string>
    </test>
    <test name="pixelsize" compare="less_eq">
      <double>12.0</double>
    </test>

    <edit name="lcd_filter" mode="assign">
      <const>lcdfilterlegacy</const>
    </edit>
    <edit name="hintstyle" mode="assign">
      <const>hintfull</const>
    </edit>
  </match>
</fontconfig>

```

---

### Post by chimiasanchi on 2008-04-28
I'm experiencing the same problem with a python/wx program that I'm using. I just used the Distribution Upgrade tool to upgrade from Feisty to Hardy.

I'll be looking into this...

---

### Post by Endolith on 2008-04-28
> **chimiasanchi said:**
> I just used the Distribution Upgrade tool to upgrade from Feisty to Hardy.

I used the upgrade tool from the alternate CD to go from Gutsy to Hardy.

---

### Post by cleduc on 2008-05-10
I'm getting this on a fresh install of Hardy, so I don't think it's related to the upgrade process.

---

### Post by Endolith on 2008-05-10
> **cleduc said:**
> I'm getting this on a fresh install of Hardy, so I don't think it's related to the upgrade process.

What program do you see it with?

---

### Post by cleduc on 2008-05-12
> **Endolith said:**
> What program do you see it with?

I'm getting this with [PrinceXML]("http://www.princexml.com/") (prince_6.0r5-1_i386.deb).  Since Prince isn't open source, I have no idea what exactly they're calling, although I'd give strong odds they're using the fontconfig library.

Here's the contents of my /etc/fonts/conf.d/53-monospace-lcd-filter.conf :
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- conf.d/monospace-lcd-filter.conf -->
<fontconfig>
<!--  Use legacy LCD filter on smaller Monospace fonts -->
  <match target="font">
    <test name="family">
      <string>DejaVu Sans Mono</string>
      <string>Bitstream Vera Sans Mono</string>
    </test>
    <test name="pixelsize" compare="less_eq">
      <double>12.0</double>
    </test>

    <edit name="lcd_filter" mode="assign">
      <const>lcdfilterlegacy</const>
    </edit>
    <edit name="hintstyle" mode="assign">
      <const>hintfull</const>
    </edit>
  </match>
</fontconfig>
```This is apparently an issue with PrinceXML, and I'm going to take it up with the nice folks at Prince.  But it is probably also an issue with the default install of fontconfig, though I can't prove that.

---

### Post by Endolith on 2008-05-12
> **cleduc said:**
> I'm getting this on a fresh install of Hardy, so I don't think it's related to the upgrade process.

Not the upgrade process itself, but a difference in configurations between Gutsy and Hardy.  The program I'm having problems with is standalone third-party.

---

### Post by Endolith on 2008-07-03
No ideas?

---

### Post by tux23 on 2008-10-03
i also had problems with princexml and this fontconfig issue after upgrading to hardy

i just removed that 53-monospace-lcd-filter.conf file (hoping never to need  any "LCD filter on smaller Monospace fonts")

and now it works

---

### Post by Endolith on 2008-11-16
Sonic Visualiser seems to work in Intrepid, but now Pidgin keeps getting "terminated by signal SIGSEGV (Address boundary error)".  

I also tried installing iMule and that gives me the same error.  What does this mean?

---

### Post by MonkeeSage on 2008-12-14
Try changing *lcdfilterlegacy* to *lcdfilter* in the config file.

---

### Post by pluckypigeon on 2009-01-23
> **MonkeeSage said:**
> Try changing *lcdfilterlegacy* to *lcdfilter* in the config file.

It actually should be "lcdlegacy"

or you can have ...

lcddefault

lcdnone

lcdlight

---

### Post by Endolith on 2009-05-28
> **Endolith said:**
> Sonic Visualiser seems to work in Intrepid, but now Pidgin keeps getting "terminated by signal SIGSEGV (Address boundary error)".  

I also tried installing iMule and that gives me the same error.  What does this mean?

It's pretty ridiculous when you search for a problem and the first Google result is a post by yourself.  I installed Jaunty on a new partition and then moved over my .purple folder, and now I'm getting this error again:

```
“pidgin” terminated by signal SIGSEGV (Address boundary error)
```

After changing Pidgin's sound configuration to "Automatic", it no longer crashes.

---

