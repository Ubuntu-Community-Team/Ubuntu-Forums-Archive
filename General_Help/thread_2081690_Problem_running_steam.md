---
title: "Problem running steam"
date: 2012-11-07
forum: General Help
---

### Post by xxnishantxx on 2012-11-07
Hi, I'm running 32-bit 12.04 with Classic Gnome. I downloaded the deb file available at *[http://media.steampowered.com/client/installer/steam.deb](http://media.steampowered.com/client/installer/steam.deb)  *and installed it with
sudo dpkg -i steam.deb
sudo apt-get install -f

But when i launch steam nothing happens. The terminal gives me this output:

$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  12
  Current serial number in output stream:  13

I have no idea what this means or why it is happening. Please help.

---

### Post by cj13579 on 2012-11-07
They probably are but you could make sure that xfonts are installed to the newest version:

```
sudo apt-get install xfonts-100dpi
```

---

### Post by xxnishantxx on 2012-11-07
Din't help :(

---

### Post by cj13579 on 2012-11-08
Hmmm - it definately looks to be a problem with the fonts. Can you run the following and post the output:

```
dpkg --get-selections | grep font
```

---

### Post by xxnishantxx on 2012-11-08
Thanks for your reply :)

Here's the output:

```
fontconfig					install
fontconfig-config				install
fonts-liberation				install
fonts-open-sans					install
fonts-raleway					install
gsfonts						install
libfont-afm-perl				install
libfontconfig1					install
libfontconfig1-dev				install
libfontenc1					install
libxfont1					install
ttf-freefont					install
xfonts-100dpi					install
xfonts-base					install
xfonts-encodings				install
xfonts-utils					install

```

---

### Post by cj13579 on 2012-11-08
Comparing yours with mine I can see one obvious difference although I don't run steam so don't know if it is the cause of the problem. You could try installing the 75dpi fonts:

```
sudo apt-get install xfonts-75dpi
```

---

### Post by xxnishantxx on 2012-11-08
no package called "fonts-75dpi". There was one called "xfonts-75dpi" (with the 'x'). I think that's the one you meant. Installed it but still no change :( I suppose it's worth mentioning that I'm running a minimal install of Precise.

---

### Post by cj13579 on 2012-11-08
Yeah, that might explain it as steam seems to be looking for something that isn't there.

When I compared your output with mine these are what I had and you didn't:

```
> xfonts-75dpi                                  install
> xfonts-scalable                                       install

```

You could try doing the scalable one also. After that, I am not sure. Have you searched the web? I googled the message and there were plenty of people who have seen this message before (in a steam and non steam context).

---

### Post by xxnishantxx on 2012-11-08
I hadn't rebooted before installing xfonts-75dpi. I installed the xfonts-scalable and rebooted and now steam has appeared and is downloading updates. Thanks for your help :D

---

### Post by Theredbaron1834 on 2012-11-13
Thanks, that fixed my Lubuntu 12.10 problem as well.

---

