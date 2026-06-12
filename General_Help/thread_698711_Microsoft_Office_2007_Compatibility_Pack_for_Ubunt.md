---
title: "Microsoft Office 2007 Compatibility Pack for Ubuntu"
date: 2008-02-16
forum: General Help
---

### Post by dr.koljan on 2008-02-16
If you use Ubuntu 8.04 LTS, then you already have [Office Open XML]("http://en.wikipedia.org/wiki/Office_Open_XML") (**docx**, **pptx** and **xlsx** files) support, however, the conversion quality of OpenOffice.org 2.4's integrated filters is quite poor and they don't allow you to save any of the aforementioned files.

There is, however, an [OpenXML/ODF Translator]("http://odf-converter.sourceforge.net") project aiming at providing Microsoft Office users with [OpenDocument format]("http://en.wikipedia.org/wiki/OpenDocument") support. It was [ported and integrated]("http://www.oooninja.com/2008/01/openxml-translator-odf-converter-11.html") by Novell into their own [OpenXML/ODF Translator for OpenOffice]("http://download.novell.com/Download?buildid=GuM6LMM9SR4~") which does exactly the opposite - adds Office Open XML support to OpenOffice.org.

Unfortunately, its Debian port at [GetDeb.net]("http://www.getdeb.net/app/OpenOffice.org+OpenXML+Translator") is outdated (its version is 1.0 while the latest is 1.1.7 with xlsx and pptx support as well as better docx conversion quality) and doesn't have a Hardy version (the Gutsy one adds MIME types which are already included in Hardy, which probably leads to conflicts).

Fortunately, there is an alternate project called **[odf-converter-integrator]("http://katana.oooninja.com/w/odf-converter-integrator")**. It is basically the same thing as the RPM from Novell or the .deb from GetDeb.net, except it doesn't add any unneeded icons* or MIME types. Installing the odf-converter-integrator package allows you to save all the OOXML files as well as get better conversion results.

[SIZE="1"]* - As of Ubuntu 8.04 LTS, neither Gnome (gnome-icon-theme) nor Tango (tango-icon-theme) icon package includes icons for OOXML files. The bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/222441").[/SIZE]

[COLOR="Gray"]Note: If you have Ubuntu 7.10 and cannot upgrade at the moment but are in a serious need for *Office Open XML* MIME types and icons, you can use [my obsolete package]("http://www.mediafire.com/?ozmp5pnwdqj") or its [64-bit port by pmaconi]("http://www.mediafire.com/?yd2xpexjy9y"). You will have to change the default applications for docx, pptx and xlsx files from *OpenOffice.org Writer/Presentation/Spreadsheet* to _*OpenOffice.org*_.[/COLOR]

---

### Post by dr.koljan on 2008-02-17
Looks like no one has noticed this thread. :(

---

### Post by danwood76 on 2008-02-17
You realise of course you can just download the plugin from the novell site and load it in open office?
No need to alienate the rpms.
I dont know why you would need rpms for a binary plugin.

regards,
Danny

---

### Post by dr.koljan on 2008-02-17
> **danwood76 said:**
> You realise of course you can just download the plugin from the novell site and load it in open office?

No you can't, the .oxt file works only with Windows.

---

### Post by danwood76 on 2008-02-17
At work I have used the novell extension with linux to load docx files.
So im not really sure what you mean.

-- edit --

Sorry my bad, I must have installed the deb on my machine at work.
I just tried loading the extension on this machine and it loads ok, just displays a read error when opening docx.
Ignore my last posts.

Oh and thanks for creating the updated .deb for us ubuntu users!

---

### Post by chunchengch on 2008-02-17
dr.koljan,

Thanks for your effort, this package is of great help for me to open lots of docx and xlsx files that I created in Windows, I do recommend Ubuntu to add it into the repository, because it will encourage more people to switch to Ubuntu from Windows, and do not need to rebuild or abandon their office documents in hand.

Great job, thanks again!

---

### Post by dr.koljan on 2008-02-17
> **chunchengch said:**
> dr.koljan,

Thanks for your effort, this package is of great help for me to open lots of docx and xlsx files that I created in Windows, I do recommend Ubuntu to add it into the repository, because it will encourage more people to switch to Ubuntu from Windows, and do not need to rebuild or abandon their office documents in hand.

Great job, thanks again!

 Well... thanks but... this is really not THAT much! :D

---

### Post by DarkDead on 2008-02-17
Thank you dr.koljan. This package saved me a lot of time. As chunchengch said it should be added to the repositories.

---

### Post by jaredssix on 2008-02-18
Actually, I only see 66 blank pages, except for some tiny images.

I see in the terminal during install:
"No theme index file in . . ." nearly a dozen times, each time suggesting
"If you really want to create an icon cache here, use --ignore-theme-index"

Is this my source of error?
If so, how would I implement --ignore-theme-index?

---

### Post by chavanak on 2008-02-18
Thanks a lot dr. Koljan. its been a great thing. Thanks once again

---

### Post by dr.koljan on 2008-02-18
> **jaredssix said:**
> I see in the terminal during install:
"No theme index file in . . ." nearly a dozen times, each time suggesting
"If you really want to create an icon cache here, use --ignore-theme-index"

Is this my source of error?

This is OK if you don't have the *gnome-accessibility-themes-extras* package installed. I included icons for the optional accessibility themes in my package, so if you don't have these themes, the *postinst* script will fail to rebuild their icon caches and give you error messages. I actually tried to hide them by using ">/dev/null" in the script, but it doesn't seem to work (I'm quite new to the shell scripts :D ). Anyway, this is not the source of your problem. Could you provide some more info on the file you tried to open?

---

### Post by Lead and Aether on 2008-02-28
Very useful, thanks!

---

### Post by David Valentine on 2008-02-29
Thank you, dr.koljan!  I think this will become a popular thread...

---

### Post by azhtar on 2008-03-01
Thanks a lot dude, you make life easier for noobs like me

---

### Post by mattman85 on 2008-03-02
> **dr.koljan said:**
> The only Debian package for *Microsoft Office 2007* (**docx**, **pptx** and **xlsx** files) support  is at [GetDeb.net]("http://www.getdeb.net/release.php?id=1995"). Unfortunately, it is outdated (its version is 1.0 while NOVELL already has 1.1 with better xlsx and pptx support) and doesn't provide any icons (you will only see white sheets of paper for icons). Therefore, I decided to make my own Debian package, based on the [NOVELL's RPM]("http://download.novell.com/Download?buildid=GuM6LMM9SR4").

I converted the RPM using alien, then deleted unneeded folders, replaced the icons with appropriate symlinks to save disk space, edited some icons with GIMP so they correctly represent the file extension and tweaked the *postinst* and *postrm* scripts so they rebuild the icon cache after installing and uninstalling the package.

The package is >>**[here]("http://www.mediafire.com/download.php?2jhwykxtdxb")**<<. You should be able to open all the **docx** **pptx** and **xlsx** files immediately after installing the package. Enjoy! :)

Does this allow for saving docx?  I tried using the Novell plugin with OpenOffice 2.3 and I can open docx fine (i realized afterwards, when looking online that 2.3 already allows opening of docx) but when I try to save docx, i get "**write error. docx can't be saved**" every time.  

any ideas of how to fix this, if it can be fixed?

---

### Post by chinasteve2000 on 2008-03-03
dr.koljan,

Pardon my ignorance, but installing by double-click in Ubuntu 7.04 I'm getting an error message: 
      [COLOR="Red"]Error: Dependency is not satisfiable: libc6[/COLOR]

I've checked Synaptic, and found libc6 is installed. Why does it not like this? What do you recommend? 

Please pardon my lower-level of experience, but I'd like to be able to teach some other friends to use your useful package as well! 

Thanks for your work!
steve

---

### Post by dr.koljan on 2008-03-06
Sorry about the delay in my reply.

> **chinasteve2000 said:**
> dr.koljan,

Pardon my ignorance, but installing by double-click in Ubuntu 7.04 I'm getting an error message: 
      [COLOR="Red"]Error: Dependency is not satisfiable: libc6[/COLOR]

I've checked Synaptic, and found libc6 is installed. Why does it not like this? What do you recommend? 

Please pardon my lower-level of experience, but I'd like to be able to teach some other friends to use your useful package as well! 

Thanks for your work!
steve

This package requires libc6 version 2.6-1, but the Feisty's repositories only contain 2.5-0. The best you could do would be upgrading to Ubuntu 7.10. :)

> **mattman85 said:**
> Does this allow for saving docx?  I tried using the Novell plugin with OpenOffice 2.3 and I can open docx fine (i realized afterwards, when looking online that 2.3 already allows opening of docx) but when I try to save docx, i get "**write error. docx can't be saved**" every time.  

any ideas of how to fix this, if it can be fixed?

Thanks for reporting, there was a bug in the previous version of this package (a missing symlink) that did not allow OpenOffice.org use OdfConverter so it used its own filters, which didn't allow saving files. A link to the fixed package is in the description.

---

### Post by tobydeemer on 2008-03-12
Hi-

How might I go about loading this into OOo on Gutsy 64-bit? (Forgive me for if that should be easy for me at this point six months into Linux.) Thanks for any help.

---

### Post by dr.koljan on 2008-03-12
> **tobydeemer said:**
> Hi-

How might I go about loading this into OOo on Gutsy 64-bit? (Forgive me for if that should be easy for me at this point six months into Linux.) Thanks for any help.

I have not tested this package on 64 bit and I doubt it works in this architecture. I guess you should use the GetDeb.net's package instead (it's older but will work for sure).

---

### Post by tobydeemer on 2008-03-13
Ah, thanks. I will try that.

---

### Post by bred on 2008-03-13
Thanks a lot dude, you u r the best
:guitar:

---

### Post by chunchengch on 2008-03-13
> **dr.koljan said:**
> 
**_The package is >>[B][here]("http://www.mediafire.com/?ozmp5pnwdqj")**<<_[/B]. You should be able to open and save all the **docx**, **pptx** and **xlsx** files immediately after installing the package. Enjoy! :)

I download the new package, but I still can not save the file.

[ATTACH]62523[/ATTACH]

> **dr.koljan said:**
> 
Thanks for reporting, there was a bug in the previous version of this package (a missing symlink) that did not allow OpenOffice.org use OdfConverter so it used its own filters, which didn't allow saving files. It's fixed in the new version.

Is **odf-converter_1.1-8_i386.deb** the new version?


Thanks!

---

### Post by dr.koljan on 2008-03-14
> **chunchengch said:**
> I download the new package, but I still can not save the file.

Did you open the file with *OpenOffice.org* or *OpenOffice.org Writer*?

> **chunchengch said:**
> Is **odf-converter_1.1-8_i386.deb** the new version?

The new package shares the filename and the version number with the broken one, sorry about that. Please re-download the package from the link in the description if you are not sure you have the right one.

---

### Post by chunchengch on 2008-03-14
I do open the file with OpenOffice.org Writer, by the way, I re-download the package, but it pops the same error.

---

### Post by AusIV4 on 2008-03-14
> Moreover, Ubuntu currently doesn't support the Office Open XML MIIME types and sees them as ZIP archives, which makes it harder to open those files.[...]I have NO IDEA why GNOME (or maybe even KDE) thinks the default applications for those files should be the aforementioned ones. If you are a Linux guru, then please explain me.
I realize this is a few weeks late, but I didn't see an explanation.

An OOXML file is basically just several components that have been zipped together. If you unzip the file, you'll find a bunch of XML files, maybe a few graphics, etc.

I can't give a whole lot of detail, as I've never actually used them, but I do know that an OOXML file compresses seperate components into one file.

---

### Post by dr.koljan on 2008-03-14
> **chunchengch said:**
> I do open the file with OpenOffice.org Writer, by the way, I re-download the package, but it pops the same error.

Try using *OpenOffice.org* instead.

> **AusIV4 said:**
> I realize this is a few weeks late, but I didn't see an explanation.

An OOXML file is basically just several components that have been zipped together. If you unzip the file, you'll find a bunch of XML files, maybe a few graphics, etc.

I can't give a whole lot of detail, as I've never actually used them, but I do know that an OOXML file compresses seperate components into one file.

I know that Office Open XML files are essentially ZIP archives, however, what I would like to know is why Ubuntu changes the default applications for docx/pptx/xlsx files from *Archive Manager* to *OpenOffice.org Writer/Presentation/Spreadsheet* respectively after adding support for the Open Office XML MIME types (this is what this package does besides the odf-converter plug-in). After you add any new MIME types to Ubuntu, they are new to it, right? Then how (and why) does Ubuntu guess the default applications for Office Open XML MIME types?

---

### Post by bastop on 2008-03-14
Hi,

Running 7.10 64-bit and OO 2.3, and neither packages work for 64 bit, not even the getdeb.net release.  Both say invalid architecture i386.  Damn i386.

---

### Post by dr.koljan on 2008-03-14
> **bastop said:**
> Hi,

Running 7.10 64-bit and OO 2.3, and neither packages work for 64 bit, not even the getdeb.net release.  Both say invalid architecture i386.  Damn i386.

Not even [this]("http://www.getdeb.net/release.php?id=1996") one?

---

### Post by pmaconi on 2008-03-17
Could you detail the steps you used to modify the .deb package you generated with alien? I would like to do the same, but for x64.

---

### Post by dr.koljan on 2008-03-17
> **pmaconi said:**
> Could you detail the steps you used to modify the .deb package you generated with alien? I would like to do the same, but for x64.

You can alienate any package using the "alien <filename>" command, but you will have to manually modify the scripts and the build tree to get a fully-working package. Although the 64-bit package is identical to 32-bit at GetDeb.net (the OdfConverter executable has the same size at least), they differ for the 1.1 version, so using the "--force-architecture" option will probably give you unsatisfactory results.

If you are really interested in the latest odf-converter version, you can extract the files from my package, replace the OdfConverter executable with the Novell's 64-bit one and then build the package using the "dpkg -b" command. Remember to place the control file as well as the scripts into a "DEBIAN" folder under the build tree's root (where "usr" and "opt" are). If you need any further help, read [this]("http://www.linuxdevices.com/articles/AT8047723203.html") article. If your package will be good, you can upload it somewhere and I'll post a link to it here. Good luck! :)

---

### Post by pmaconi on 2008-03-17
Ok, I was mostly successful. I cannot, however, save files in the docx format with my .deb package. I don't get an error - it just opens a save as dialog that doesn't have a .docx option. Which syslink did you need to create to get this to work for i386? 

Also, does opening a file with OpenOffice.org instead of Writer cause a template window to open in addition to the file? Is there any way to disable this?

---

### Post by dr.koljan on 2008-03-18
> **pmaconi said:**
> Ok, I was mostly successful. I cannot, however, save files in the docx format with my .deb package. I don't get an error - it just opens a save as dialog that doesn't have a .docx option. Which syslink did you need to create to get this to work for i386?

Are you sure OpenOffice 2.3 uses OdfConverter and not its own filters? Open [this]("http://openofficeorgninja.googlepages.com/OpenXML_text_reference_v1_2.docx") file - you should get something like [this]("http://laurenstephens.net/uploads/dfee669fbe.pdf") after seeing a "Waiting for an external application" message for a while. If you do, then OdfConverter works and you don't need any symlinks, the problem is somewhere else. If not, then there is something wrong with your package.

> **pmaconi said:**
> Also, does opening a file with OpenOffice.org instead of Writer cause a template window to open in addition to the file? Is there any way to disable this?

I am aware of this, however, the same happens with the GetDeb's 1.0 package so it's not my fault :) There should be an option somewhere in OpenOffice.org, but I don't even know where to look.

---

### Post by pmaconi on 2008-03-18
It turns out that OpenOffice was using its own filters. I've fixed that problem, but now when trying to use OpenOffice.org to open a .docx I get a Read-Error: Data could not be loaded from the file. Any ideas?

Edit: I figured it out. When I tried to run the OdfConverter via a terminal, it said that I was missing libgif4 - adding this as a dependency fixed it.

---

### Post by pmaconi on 2008-03-18
Here is a working OdfConverter for OpenOffice.org 2.3 on Ubuntu 7.10 x64: [[COLOR="RoyalBlue"]odf-converter_1.1-8_amd64.deb[/COLOR]]("http://www.mediafire.com/?yd2xpexjy9y")

---

### Post by dr.koljan on 2008-03-18
> **pmaconi said:**
> Here is a working OdfConverter for OpenOffice.org 2.3 on Ubuntu 7.10 x64: [[COLOR="RoyalBlue"]odf-converter_1.1-8_amd64.deb[/COLOR]]("http://www.mediafire.com/?yd2xpexjy9y")

Thanks, I have added this to the first post. :)

---

### Post by mattman85 on 2008-03-23
I have been trying to get OpenOffice to successfully save docx for about a month now.  With classes at school, my professors have just been saving and emailing *x files and with some students not having docx, xlsx, and pptx.  OpenOffice always came up with write errors with the *x stuff.  I have Office 07 in Windows (i dual-boot), but my laptop gets so much better battery life, and stays a lot cooler, while I run Ubuntu.  your .deb package saved me the headache of having to boot into Windows to work with docx format!  Thanks for posting the package!

---

### Post by jms830 on 2008-04-17
So my biggest question is now that .docx is "open," will OpenOffice 3 finally have ''perfect'' conversion from microsoft word files? I think it is my biggest hurdle introducing people to ubuntu. The footnotes, track changes, etc, etc don't convert properly from .doc.

---

### Post by dr.koljan on 2008-04-17
> **jms830 said:**
> So my biggest question is now that .docx is "open," will OpenOffice 3 finally have ''perfect'' conversion from microsoft word files? I think it is my biggest hurdle introducing people to ubuntu. The footnotes, track changes, etc, etc don't convert properly from .doc.

Not perfect, but good :)

---

### Post by rocksocke on 2008-04-17
Hi!

i would be highly interested in using this package but because of its dependencies i cant use it. it requires to install libgif4 which itself requires the removal of about 30 packages (amongst ffmpeg, mencoder and other more or less important things)!

:/

---

### Post by dr.koljan on 2008-04-17
> **rocksocke said:**
> Hi!

i would be highly interested in using this package but because of its dependencies i cant use it. it requires to install libgif4 which itself requires the removal of about 30 packages (amongst ffmpeg, mencoder and other more or less important things)!

:/

What version of Ubuntu do you use?

---

### Post by rocksocke on 2008-04-17
hi!

i installed ubuntu gutsy (i have my specs in my signature). allthough here is uname -a

Linux malap 2.6.24 #2 SMP Mon Jan 28 17:29:13 CET 2008 x86_64 GNU/Linux

(i compiled the kernel with kernelcheck)

---

### Post by dr.koljan on 2008-04-18
> **rocksocke said:**
> (i compiled the kernel with kernelcheck)

I think this is the problem. :(

---

### Post by rocksocke on 2008-04-18
normally it this shouldn influence apt or am i wrong?

---

### Post by dr.koljan on 2008-04-19
> **rocksocke said:**
> normally it this shouldn influence apt or am i wrong?

It would be good if you could provide me with a full log of your installation attempt.

---

### Post by dr.koljan on 2008-04-25
Now that Ubuntu 8.04 LTS has been released, this package is now obsolete (it includes Office Open XML MIME types which are already included in the latest Ubuntu release). I would update my package to remove unneeded files, however, this seems useless as there exists a much bigger project called [odf-converter-integrator]("http://katana.oooninja.com/w/odf-converter-integrator"). Please use that project unless you have Ubuntu 7.10 AND need icons and file associations.

---

### Post by unMourned on 2008-04-28
Installed and using 8.04 right now.

I can open a docx file, but cannot save as docx.  Saving as xml saves a rather useless xml file.

Isn't there a way to use openoffice in place of MS Office 2007?

-p

---

### Post by dr.koljan on 2008-04-29
> **unMourned said:**
> Installed and using 8.04 right now.

I can open a docx file, but cannot save as docx.  Saving as xml saves a rather useless xml file.

Isn't there a way to use openoffice in place of MS Office 2007?

-p

Yes, just install odf-converter-integrator

---

### Post by pmaconi on 2008-05-04
Sadly, the integrator doesn't support x64. Do you know of any future plans to do so?

---

### Post by dr.koljan on 2008-05-04
> **pmaconi said:**
> Sadly, the integrator doesn't support x64. Do you know of any future plans to do so?

Yeah, we are working on it now.

---

### Post by xadder on 2008-05-05
Just a thanks from me too. I was working with a Word .docx from a virtual installation (kvm) of XP, and this just ran out of steam - document too complex, can't save,. etc....  I tried with my new Hardy installation and oo2.4, but the "track changes" stuff had been mangled - with both old and new text shown as normal black font. I found this thread, installed the converter, and all is well again!

---

### Post by dr.koljan on 2008-05-06
In case someone needs the 64-bit version of this package, you can download it [here]("http://katana.oooninja.com/f/software/odf-converter-integrator-chocolate_0.1.4-1_amd64.deb").

Please post the results in this thread, because this package is still being tested.

---

### Post by pmaconi on 2008-05-06
That package still has the i386 architecture setting, even though it is named for x64.

---

### Post by Andrew.Z on 2008-05-06
> **pmaconi said:**
> That package still has the i386 architecture setting, even though it is named for x64.

I packaged it.  In the control file I have it set to amd64, but when I package using this command

```
dpkg --build odf-converter-integrator-0.1.4 odf-converter-integrator-chocolate_0.1.4-1_amd64.deb
```

dpkg adds i386 in addition to amd64, so both are actually in the control file.  I don't have a 64-bit machine.  Hmm.

---

### Post by dr.koljan on 2008-05-07
> **Andrew.Z said:**
> dpkg adds i386 in addition to amd64, so both are actually in the control file.  I don't have a 64-bit machine.  Hmm.

Please send me or upload somewhere the build tree. I'll package it.

---

### Post by Andrew.Z on 2008-05-07
> **dr.koljan said:**
> Please send me or upload somewhere the build tree. I'll package it.

Thanks.  It should be enough to unpack and then run the shell script
[http://katana.oooninja.com/f/tmp/oci-v014-64bit.tar.bz2](http://katana.oooninja.com/f/tmp/oci-v014-64bit.tar.bz2)

---

### Post by dr.koljan on 2008-05-08
> **Andrew.Z said:**
> Thanks.  It should be enough to unpack and then run the shell script
[http://katana.oooninja.com/f/tmp/oci-v014-64bit.tar.bz2](http://katana.oooninja.com/f/tmp/oci-v014-64bit.tar.bz2)

Your server is giving me HTTP 500 :(

---

### Post by Andrew.Z on 2008-05-09
> **dr.koljan said:**
> Your server is giving me HTTP 500 :(


Works for me. I get a hotlinking not allowed error, but then I just click on the URL listed on the no-hotlinking page.

Try copying the URL into a new browser window so there is no referrer.  Otherwise, PM me an email address where I can email you the 4MB file.

---

### Post by dr.koljan on 2008-05-09
Done.

Please check your email.

---

### Post by crtlbreak on 2008-05-12
Thank you - it has helped with viewing the xdocs on my ooboontoo!!

---

### Post by AbredPeytr on 2008-05-12
Wouldn't the easiest fix simply be to set the default "save as" in Office 2007 to the usual .doc, .xls, and .ppt rather than using the useless .docx, etc.? That is what I did at work because I didn't want to have compatibility issues with colleagues that don't know how to find and install converters like the one from Microsoft for earlier versions of Office. If someone sends me such a file, I tell them to save it as an earlier version. There is simply no need for .docx, .xlsx, .pptx. Or am I missins some life changing feature with Microsofts so-called open document format?

But thanks for the info anyway to help those who think they needed it!

---

### Post by yammosk on 2008-05-13
Installed the chocolate edition for Ubuntu from the website. Works like a charm. THANK YOU! :guitar:

---

### Post by dr.koljan on 2008-05-16
The 64-bit package has been released :)

[http://katana.oooninja.com/w/odf-converter-integrator/download](http://katana.oooninja.com/w/odf-converter-integrator/download)

---

### Post by crtlbreak on 2008-06-05
Thank you Very much for your info.
This is exactly what these forums are about :grin:
Now if I can just work out where the button is to officially say thank you?

---

### Post by pmaconi on 2008-06-05
You can use the thank you button that is at the bottom right of every post. It looks like a little medal (a star hanging from a blue ribbon).

---

### Post by pmaconi on 2008-06-22
That 64-bit package still gives me an incorrect architecture error. Using the link on the previous page, I rebuilt the package using my amd64 computer. It can be found [here]("http://www.mediafire.com/?zb2sw5ygj4m").

---

### Post by dr.koljan on 2008-06-23
Strange, the package on the site was made by me and worked fine. :confused:

---

### Post by pmaconi on 2008-06-23
Odd.

---

### Post by tech0007 on 2008-06-24
I use hardy and i'm trying to open an xlsx file. I tried both strawberry and chocolate editions of odf converters but they didn't work. I get converter: odfConvert error rc=27.  Help.

---

### Post by cjnkns on 2008-06-29
I am a bit late to the odf converter party, but is the odf converter a command line tool? I tried to skim through all the posts but I am still not sure. So I was hoping someone with a bit of experience using this could help me out.

I just downloaded odf-converter_1.1.-8.i386.deb - is this the file I want in order to open .docx in openoffice and be able to save docx also?

Thanks for your help..

---

### Post by arashiko28 on 2008-06-29
you'll be able to open .docx but at the time of saving, you can't save it as .docx, you must choose among the other choices, I've had it quite a while now, it's pretty usefull just for reading a document, now i'm trying to install the m$office2007, because i need to open .pptx too.


[COLOR="Red"]UPDATE[/COLOR]

I was based on what i knew of the previous versions. This version allows you to save the documents.

---

### Post by arashiko28 on 2008-06-29
> **dr.koljan said:**
> If you use Ubuntu 8.04 LTS, then you already have [Office Open XML]("http://en.wikipedia.org/wiki/Office_Open_XML") (**docx**, **pptx** and **xlsx** files) support, however, the conversion quality of OpenOffice.org 2.4's integrated filters is quite poor and they don't allow you to save any of the aforementioned files.

There is, however, an [OpenXML/ODF Translator]("http://odf-converter.sourceforge.net") project aiming at providing Microsoft Office users with [OpenDocument format]("http://en.wikipedia.org/wiki/OpenDocument") support. It was [ported and integrated]("http://www.oooninja.com/2008/01/openxml-translator-odf-converter-11.html") by Novell into their own [OpenXML/ODF Translator for OpenOffice]("http://download.novell.com/Download?buildid=GuM6LMM9SR4~") which does exactly the opposite - adds Office Open XML support to OpenOffice.org.

Unfortunately, its Debian port at [GetDeb.net]("http://www.getdeb.net/app/OpenOffice.org+OpenXML+Translator") is outdated (its version is 1.0 while the latest is 1.1.7 with xlsx and pptx support as well as better docx conversion quality) and doesn't have a Hardy version (the Gutsy one adds MIME types which are already included in Hardy, which probably leads to conflicts).

Fortunately, there is an alternate project called **[odf-converter-integrator]("http://katana.oooninja.com/w/odf-converter-integrator")**. It is basically the same thing as the RPM from Novell or the .deb from GetDeb.net, except it doesn't add any unneeded icons* or MIME types. Installing the odf-converter-integrator package allows you to save all the OOXML files as well as get better conversion results.

[SIZE="1"]* - As of Ubuntu 8.04 LTS, neither Gnome (gnome-icon-theme) nor Tango (tango-icon-theme) icon package includes icons for OOXML files. The bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/222441").[/SIZE]

[COLOR="Gray"]Note: If you have Ubuntu 7.10 and cannot upgrade at the moment but are in a serious need for *Office Open XML* MIME types and icons, you can use [my obsolete package]("http://www.mediafire.com/?ozmp5pnwdqj") or its [64-bit port by pmaconi]("http://www.mediafire.com/?yd2xpexjy9y"). You will have to change the default applications for docx, pptx and xlsx files from *OpenOffice.org Writer/Presentation/Spreadsheet* to _*OpenOffice.org*_.[/COLOR]


I have hardy. On my synaptic package there is the version 1.0.0-6 is the one i currently have and works great to be able to read .docx but it's a total mess on .pptx everything is out of place and letters one over another and pictures don't load. Haven't tried with .xlsx, i don't use that a lot. 
The version you offer is 0.1.4-1, isn't is outdated too?

when i try to update it on terminal, it says that it's already the latest version.

---

### Post by arashiko28 on 2008-06-29
I have installed it an tried it, I bow before you =D> there's no ovation icon, jeje.

Well i must admit it's a great advance, works perfectly in comparation with the previous version, the .pptx are readable and the pictures can be seen. And I forgot to mention that yes, you can save the documents as you received them, thing that wasn't possible before.

Thanks a lot.

---

### Post by abuzakour on 2008-06-29
Hi Guys, 

please I've already installed libgif4... i am using Hardy ... I tried the chocolate version first and i got this

rabeeh@rabeehubuntu:~$ cd Desktop
rabeeh@rabeehubuntu:~/Desktop$ sudo dpkg -i odf-converter-integrator-chocolate*deb
(Reading database ... 141917 files and directories currently installed.)
Unpacking odf-converter-integrator (from odf-converter-integrator-chocolate_0.1.4-1_i386.deb) ...
dpkg: error processing odf-converter-integrator-chocolate_0.1.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/XLSXFilter.xcu', which is also in package odf-converter
Errors were encountered while processing:
 odf-converter-integrator-chocolate_0.1.4-1_i386.deb

so I tried to install the strawberry version .. 

rabeeh@rabeehubuntu:~/Desktop$ sudo ln -s /usr/lib/libtiff.so.4 /usr/libtiff.so.3
rabeeh@rabeehubuntu:~/Desktop$ dpkg -i odf-converter-integrator*deb
dpkg: requested operation requires superuser privilege
rabeeh@rabeehubuntu:~/Desktop$ sudo dpkg -i odf-converter-integrator*deb
(Reading database ... 141917 files and directories currently installed.)
Unpacking odf-converter-integrator (from odf-converter-integrator_0.1.5-2_i386.deb) ...
Preparing to replace odf-converter-integrator 0.1.5-2 (using odf-converter-integrator-chocolate_0.1.4-1_i386.deb) ...
Unpacking replacement odf-converter-integrator ...
dpkg: error processing odf-converter-integrator-chocolate_0.1.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/XLSXFilter.xcu', which is also in package odf-converter
Setting up odf-converter-integrator (0.1.5-2) ...

Errors were encountered while processing:
 odf-converter-integrator-chocolate_0.1.4-1_i386.deb

please help.. i am keeping my xp only for the office 2007

:(

---

### Post by kumarnarain on 2008-06-30
Hello Koljan
This was really useful....sometmes I used to boot WinXp just to retain some formatting...I dont see the need now

---

### Post by dr.koljan on 2008-06-30
> **abuzakour said:**
> trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/XLSXFilter.xcu', **which is also in package odf-converter**

This means you need to uninstall odf-converter first.

---

### Post by abuzakour on 2008-06-30
> **dr.koljan said:**
> This means you need to uninstall odf-converter first.


how to uninstall it ? :(

---

### Post by dr.koljan on 2008-06-30
> **abuzakour said:**
> how to uninstall it ? :(

Either using Synaptic Package Manager, or:

```
sudo apt-get remove --purge odf-converter
```

---

### Post by kwaanens on 2008-07-19
The 64 bit chocolate deb on the download page gives "wrong architecture" It is labeled amd64, but is, in fact, i386. At least that's what my computer's telling me.

---

### Post by dr.koljan on 2008-07-21
True.

I'll inform Andrew about this.

EDIT: It's fixed now.

---

