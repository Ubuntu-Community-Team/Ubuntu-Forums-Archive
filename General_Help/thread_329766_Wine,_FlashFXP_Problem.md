---
title: "Wine, FlashFXP Problem"
date: 2007-01-02
forum: General Help
---

### Post by Snip0r on 2007-01-02
Hello Ubuntu Community,

I'm quite new @Ubuntu, but i think i have already learned much :)

I tried wine as an emulator for flash fxp v3, because i didn't find any equivalent ftp program for linux.

Everything worked very fine, flashfxp started just as at windows, and nearly all of the functions worked.

When it came to connecting to a server, it also worked, but when flash fxp requested the dir list, flashfxp "crashed" it has frozen, and i had to kill the process.

I have heard, that flashfxp v2 definitely works @wine, i tried version 3 because its much better.

If you don't know any solution i will switch to version2 but please try to help me solving this problem.

Thanks,

Snip0r

---

### Post by tenn on 2007-01-02
I dont know about flashfxp v3 and running it in Wine but have you tried gFTP

---

### Post by Snip0r on 2007-01-02
Yes, sure

but it doesn't support important features like fxp and the control is not comfortable to me.

I also tested kasablanca, igloo ftp, kftpgrabber but none of these programs have the niveau of flash fxp.

---

### Post by NGEvo on 2007-01-02
lol, honestly, thats just a bit edgy,.. what do you NEED in Flash FXP that isn't in alternatives?

If you come up with a decent answer, try to emulate SmartFTP, I use that..

---

### Post by Snip0r on 2007-01-02
I'm just accustomed to flash fxp, smart ftp has a whole different gui.

If i had started with smarftp i may use it now, but i started with flashfxp and it's the only program i need to emulate under ubtuntu, so could you please help me this one time?

Would be really great...

Snip0r

---

### Post by morningboat on 2007-01-07
For KDE user, KFTPGrabber, i.e., kftp, is a substitute for FlashFXP.
For Gnomb user, you can see a list at [http://gnomefiles.org/subcategory.php?sub_cat_id=44](http://gnomefiles.org/subcategory.php?sub_cat_id=44)   , personally I think CrossFTP is good candidate since it has almost all the features FlashFXP has, and can import FlashFXP's sites. Meanwhile FileZilla is also becoming better now, and hope it will support the FXP and more proxy settings in future.

---

### Post by embeejay on 2007-01-07
I have the excact same problem with flashfxp v3, hope somebody has a solution.

---

### Post by nix4me on 2007-01-07
I agree with the state of ftp programs for linux.

The only working client near flashfxp quality is kasablanca.  Gftp crashes too much and by default wont do ssl/tls and also fxp.

nix4me

---

### Post by embeejay on 2007-01-08
I got it to work by adding a bunch of native windows dll's to wine, tho the icons in the menubar looks pretty dodgy. The list of native dlls i added is too long to write here - it's basically all of them, except for the 4 mentioned un the wine docs not to add + userenv.dll since if i add that as native it makes flashfxp crash at startup.

The way i did it was to look at the error output in the terminal when i started flashfxp and then added all the native versions of the dll's that wine did error output on, except a few where wine told me it was not recommended (like advapi32.dll). then i ran it again and looked for new dll errors and so on until the only dll errors left was in kernel, advapi32, actctx, seh (couldn't find a dll with the names seh & actctx) and userenv.

---

### Post by Voorhees1979 on 2008-03-17
flashfxp has the raw command feature. I cant find any linux ftp program with gui to do this :(

---

### Post by Baltazar72 on 2008-07-09
I am using FlashFXP 3.6 with Wine, for me it works great. You need to patch and build wine from source to do this. Patch can be found in this bug report. [http://bugs.winehq.org/show_bug.cgi?id=5131]("http://bugs.winehq.org/show_bug.cgi?id=5131")

Regards

---

### Post by gardara on 2008-07-20
I use crossftp and wlfxp... wlfxp is really basic but supports RAW commands... Crossftp is much smoother so I use that when I don't need RAW commands...
[http://jfxp.sourceforge.net/](http://jfxp.sourceforge.net/)

---

