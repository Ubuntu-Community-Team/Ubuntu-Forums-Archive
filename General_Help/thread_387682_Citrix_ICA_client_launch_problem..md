---
title: "Citrix ICA client launch problem."
date: 2007-03-18
forum: General Help
---

### Post by hinge on 2007-03-18
Hi 

Running kubuntu edgy with firefox - trying to install the citrix ICA client 10.0.

The install was done by following this:

[http://zwhlug.org/HOWTO_Citrix](http://zwhlug.org/HOWTO_Citrix)

Everything went smooth....

But....when I try to access the citrix at work this happens. 
I get through the RSA login page and i get the citrix application window - when I click on an application I see that firefox downloads a file called launch.ica - I see that a lot of people have problems running this file with because the association is not made in firefox - this is not my problem because the association is made - but nothing happens after the download.
After googling a bit I found that you can run the launch.ica with wfica.sh to get more info - this I did:

[COLOR="Magenta"]./wfica.sh /tmp/launch.ica
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found
[/COLOR]

has anybody else had this problem - or even a suggestion for a solution ??

---

### Post by kindaran on 2007-03-24
Yup, same problem here... awaiting/searching for a solution

---

### Post by gb5757870 on 2007-03-25
I struggled too but using this guide [http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml]("http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml")
 got it working. good luck!

---

### Post by bz-mof on 2007-03-28
Try a "xset fp rehash" at the console, worked for me!

---

### Post by Ocelaris on 2007-05-08
edit your

/usr/lib/ICAClient/nls/en/UTF-8/Wfcmgr so that the font section has this:


Wfcmgr*fontList:\
-*-gothic-medium-r-normal-*-*-120-*-*-*-*-ksc5601.1987-0;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-1;\
-*-ming-*-*-*-*-*-140-*-*-*-*-big5-0;\
-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0;\
-*-helvetica-medium-r-normal--0-*-75-75-p-*-koi8-r;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-arial-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-kacstbook-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\


instead of this:

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

Then set start up program under sessions to run "xset fp rehash" no quotes... but the launching of ICA files is tricky... working on that. if you run wfcmgr launch.ica it will launch a citrix session, but you obviously want it to link with firefox...

---

### Post by nicksukharev on 2007-05-11
Ok, I solved this problem for myself for ICAClient version 10. The script mentioned on citrix forums did not help (although it might be required, just not sufficient to solve the issue). What I had to do is fixing the FontPaths in my xorg.conf. Here is what I have there now:

Section "Files"

        # path to defoma fonts
#    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
#    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
#    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
#    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/misc"
EndSection

Commented out are the lines I had there after Dapper->Edgy upgrade. The last 5 lines I added (thanks to another font-related post I found elswhere).
I figured it might help after finding the following in the x log file : 
FreeType: couldn't open face /usr/share/X11/fonts/Type1/c0632bt_.pfb: 1
Now the ICAclient starts properly.

---

