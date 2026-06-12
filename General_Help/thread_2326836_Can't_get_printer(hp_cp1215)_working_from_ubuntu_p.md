---
title: "Can't get printer(hp cp1215) working from ubuntu printserver. Works from windows"
date: 2016-06-05
forum: General Help
---

### Post by Everett Arndt on 2016-06-05
Can't get printer(HP cp1215) working from Ubuntu print-server. Works from windows my server is a Ubuntu on older laptop. I have made the jump to Linux from windows trash. it is good for most. I am tired of learning a new system every few years. I also don't like all the junk that affects performance. I have tried to load hplip with no success I have been at this for three weeks. I am not very savvy with all the commands in terminal however I did try to load manually using what I found on Internet cook booking it. I got errors but could not get the error to correct. I have been printing to pdf file and using a windows machine to print my documents. 
Thank you, Everett


  .

---

### Post by themainliner2 on 2016-06-05
Everett, first things first can you tell us what the errors are? Word for word.

Second, if you encounter a problem try Googling (other search engines are available) what you are trying to do.

This might help you out: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Third, if the second option isn't working try Googling your error messages.

Fourth, if the second and third option failed, come here. ;)

---

### Post by X-RED_Tech on 2016-06-05
No, first things first, tell us your Ubuntu release, what connection (probably USB?) and how have you installed HPLIP...

Any HP printer should be "plug&play" in any properly updated currently supported release: HPLIP, if not installed already, is available at the software centre.

---

### Post by ajgreeny on 2016-06-05
Please use the default font when posting, not the large sized version you used.

That printer needs HPLIP 3.9.2 or newer.  As far as I'm aware the HPLIP version in all supported versions of *ubuntu is OK for that printer, even in 12.04, which had version 3.12.2.

Do you have HPLIP installed?  If not install it and try again.  You may need to run hp-setup after installing HPLIP to download and install the required driver-plugin which is not part of HPLIP but a proprietary add-on
See [http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html).

---

### Post by kansasnoob on 2016-06-05
Please post the full output of:

```
sudo apt-get install hplip hplip-gui
```

---

