---
title: "Citrix ICA Client 10.6 on Gutsy (32bit)"
date: 2007-10-25
forum: General Help
---

### Post by sant0sk1 on 2007-10-25
I cannot get the wfcmgr to launch for the life of me! I have read and followed many tutorials and suggestions from both UbuntuForums, Google, and Citrix's forums. 

[LIST]
[*]I have manually installed citrix ica client 10.6 using installer script. 
[*]I have installed libxaw6 (and 7) and libmotif3. 
[*]I have followed the bug fix for the 10.0 client and Ubuntu 6.10
[*]I have modified my /usr/lib/ICAClient/nls/en/UTF-8/Wfcmgr to match other people's
[*]i have executed "xset fp refresh" afterwards
[*]I have modified my xorg.conf to change path to used fonts
[/LIST]

After all of these attempts, I am still receiving the following errors when launching from the command line:

```
Warning: 
    Name: FONTLIST_DEFAULT_TAG_STRING
    Class: XmRendition
    Conversion failed.  Cannot load font.

Segmentation fault (core dumped)

```

Anybody have any ideas?

---

### Post by evilhomer on 2007-12-06
Did you ever resolve this?  I'm experiencing the same.

---

### Post by mlissner on 2007-12-07
Same boat here.

---

### Post by the_unexpected on 2007-12-31
I was able to get the client to install with no issues, but when I try to connect to a web-based metaframe server, I get the following error:

'you have not chosen to trust "Entrust.net Secure Server Certification Authority:, the issuer of the server's security certificate'. 

I followed the steps towards the bottom of the page on [this](http://support.citrix.com/forums/thread.jspa?forumID=69&threadID=58901&tstart=30) link, but still received the same error. 

Any assistance would be appreciated! :)

---

### Post by mikexgough on 2007-12-31
I got that with mine, had a digisign certificate issue, so go to the site that holds the certificate (google the certificate name) download and save it then put it in the  ICA Client install directory(wherever you installed it to)in the keystore folder in the CaCerts sub folder, close up everything ,restart  the browser, login and and voila should work fine........good luck and hope it helps

---

### Post by kpurrucker on 2008-02-04
I resolved the Segmentation-fault-problem with a hint from the "german citrix user group".  It seems to be a problem with the utf8 font.

You have only to change the section "Wfcmgr*fontList:" in the file "/usr/lib/ICAClient/nls/de/UTF-8/Wfcmgr" from the icaclient like:

```

Wfcmgr*fontList:\
! -gnu-*-*-*-*-*-*-120-*-*-*-*-iso10646-1;\
-*-gothic-medium-r-normal-*-*-120-*-*-*-*-ksc5601.1987-0;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-1;\
-*-ming-*-*-*-*-*-140-*-*-*-*-big5-0;\
-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0;\
-*-helvetica-medium-r-normal--0-*-75-75-p-*-koi8-r;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-arial-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-kacstbook-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
! -*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
! -*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
! -*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

```

(!) The "de" in the path of the file are from the german languageset. This may differ, if you use a other language. 

I had in addition a second problem. I could configure a ica connection, but i couldn't start the connection. The wfcmgr-program says only "Cannot load font", if i start it on the commandline. A look in the x-server log told me, that I had some wrong paths in  the file "/etc/X11/xorg.conf". The paths should be "/usr/share/fonts/X11/<fontname>". In my xorg.conf were some fonts in the section "Files" with the wrong path "/usr/share/X11/fonts/". I thing it is, because i update my Ubuntu from a older version, as Gutsy.

You find a smarter (but german :mrgreen: ) version of the resulotion in my blog [http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/]("http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/")

---

