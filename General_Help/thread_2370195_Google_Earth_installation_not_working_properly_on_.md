---
title: "Google Earth installation not working properly on Ubuntu 16.04"
date: 2017-08-31
forum: General Help
---

### Post by jack6128 on 2017-08-31
Thinkpad T60
Intel® Core™2 CPU T7200 @ 2.00GHz × 2 
Gallium 0.4 on ATI RV515
64-bit
3gb RAM

I installed GE according to the latest instructions. Installed 64bit versions of **lsb-invalid-mta, [B]lsb-security and [B]lsb-core. **[/B][/B]Installed **GDebi. **Installed, uninstalled and reinstalled **GE** several different times in several different ways, all with the same results. See attachment. The splash screen won't leave and the actual GE window is a very small rectangle in the upper left of the viewing screen. I can fly to a location, zoom in and out, and move around, but only in that tiny tiny rectangle. I have no problems with any other apps. Does anyone have any insight to share? Could my hardware not be up to the task?

Thanks,
Jack

---

### Post by HermanAB on 2017-08-31
Yeah, well, Google isn't exactly know for writing high quality software...

Try a different version of GE.  Re-installing the same version will yield the exact same results, so there is no point in doing that.

---

### Post by jack6128 on 2017-08-31
> **HermanAB said:**
>  Try a different version of GE.

Thanks, HermanAB, I was thinking along those same lines. Do you know where I can download a different 64bit version of GE for Linux?

---

### Post by wheatpenny2 on 2017-09-01
I downloaded and installed the GE deb file from [https://www.google.com/earth/download/gep/agree.html](https://www.google.com/earth/download/gep/agree.html) and it works with no problems on Ubuntu 17.04

---

### Post by frappe792 on 2017-12-06
> **wheatpenny2 said:**
> I downloaded and installed the GE deb file from [https://www.google.com/earth/download/gep/agree.html](https://www.google.com/earth/download/gep/agree.html) and it works with no problems on Ubuntu 17.04

That's a shame, I downloaded mine from the same site (64 bit) and all I get is the splash screen. don't see an earth at all, in fact where the earth image is normally displayed I can still see my wallpaper poking through the Google Earth software.

---

### Post by chainik11 on 2018-01-23
Which version of GE did you install?

I install the latest v7.3.0.3832 (current for Jan 24) and can confirm -- it does not work (does not render Earth at all). Menus, left panel and photos work well but main window looks absolutely transparent. I can see wallpaper or previously opened windows through it.

---

### Post by malangaman on 2018-02-06
I have spent hours with the same problem, tried all solutions. Same result. GE pro works great on win 10 of double boot, but not on Ubuntu 16.04 as of yet. Have you made any progress with your problem?

---

### Post by johnaaronrose on 2018-04-24
> **malangaman said:**
> I have spent hours with the same problem, tried all solutions. Same result. GE pro works great on win 10 of double boot, but not on Ubuntu 16.04 as of yet. Have you made any progress with your problem?
Same problem. I've even tried installing lsb-core, lsb-invalid-mta  lsb=security packages but it made no difference.

---

### Post by yancek on 2018-04-24
I downloaded and installed google-earth several months ago and had major problems with it so I installed an older version (Google Earth Pro 7.1.8.3036 (64-bit)) from the site below and use it with no problems.  I used the option to open in Software Center so that when the download finished, the Software Center opened with the option to Install.  Don't know that would matter as an install method.

[https://drive.google.com/file/d/0Bx0YZ3Xi3rgTcTNjelJwUEVkNDQ/view](https://drive.google.com/file/d/0Bx0YZ3Xi3rgTcTNjelJwUEVkNDQ/view)

---

### Post by johnaaronrose on 2018-04-24
Thanks, yancek. I first installed at, lsb-core, lsb-invalid-mta, lsb-security & pax packages in Terminal:
sudo apt install at lsb-core lsb-invalid-mta lsb-security pax
as gdebi operating on downloaded file said that they were missing dependencies.
Then used gdebi to install the downloaded (using your link) google-earth-pro-stable_7.1.8.3036-r0_amd64.deb 
After install, I ran Google Earth and it worked perfectly.

---

### Post by yancek on 2018-04-24
It appears that newer release was problematic for a lot of people.  I don't recall having to install the additional software you did but it worked for me.  Glad you got it working.

---

### Post by monkeybrain20122 on 2018-04-24
GE is now a web page [https://earth.google.com/web/](https://earth.google.com/web/) if you don't need the binary for special reason just go to the webpage with Chrome (or Chromium?) and make a webapp, pin it to your launcher or your desktop depending on your DE. No need to install anything other than Chrome(or Chromium?)

Edited: just downloaded and installed GE pro 7.3.1.4507 (latest), not a problem at all, Ubuntu 16.04.4.

Edited: GE pro 7.3.1.4507 also works in Ubuntu 18.04 beta. No issue at all.

---

