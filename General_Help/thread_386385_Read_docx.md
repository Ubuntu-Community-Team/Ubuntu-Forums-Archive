---
title: "Read docx"
date: 2007-03-16
forum: General Help
---

### Post by frankabel on 2007-03-16
Hi all,

How can I read a docx on ubuntu? Any good free online converter or any desktop converter? I had found some online converter, but can't convert the document that I try to view.

Salute
Frank Abel

---

### Post by vnt87 on 2007-03-19
Just came accross Novell's site and saw this: OpenOffice. OpenXML Translator

[http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58~](http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58~)

I haven't been able to get it to work on my Edgy though. OOo's Package Manager simply hangs when I try to feed the .oxt file to it.
I haven't tried the rpm package though, I'll try converting it tonight.

Edit: converted it using alien but still no luck getting it to work. If anybody can find away, please do post your methods.

---

### Post by stuporglue on 2007-03-25
Someone figured it out over at  [http://forum.ubuntuusers.de/topic/78247/](http://forum.ubuntuusers.de/topic/78247/)

Essentially: 
1) Download the file odf-converter-1.0.0-5.i586.rpm from [http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58~](http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58~)

2) Use alien to convert it to a Slackware tgz file
```
 fakeroot alien -ct odf-converter-1.0.0-5.i586.rpm
```

3) Unpack the slackware tgz file
```
tar xzf odf-converter-1.0.0.tgz
```

4) Copy three files into your OpenOffice.org directories -- note that the usr that you're copying from is a directory that was inside the tgz file. 
```
sudo cp usr/lib/ooo-2.0/program/OdfConverter /usr/lib/openoffice/program/
sudo cp usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/
sudo cp usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/
```

5) Restart OpenOffice, and enjoy. 

Results:
I only have one docx file and it's really simple, but it did work fine.

---

### Post by the8thstar on 2007-04-17
It doesn't work for me. "Fakeroot" is an unrecognized command/module in my Ubuntu.

---

### Post by stuporglue on 2007-04-17
> It doesn't work for me. "Fakeroot" is an unrecognized command/module in my Ubuntu.

Seems you need the fakeroot utility. :-)

You can install it with Synaptic (the GUI pacakge manager) or with apt-get (command line package manager).

---

### Post by unntrlaffinity on 2007-04-20
I followed these instructions and all that happens when I try to open a .docx file is that OpenOffice.org begins to load and then hands forever at the loading screen when the progress bar completes.  Has anyone else had better luck?

---

### Post by stuporglue on 2007-04-20
I mentioned in my first post that the docx file I had was really simple (Just a bulleted list, iirc). If your document isn't private, I can see if my OpenOffice can open it. If it can, we can compare what we've got installed and see where your hangup is.

Post it at [http://www.filecrunch.com/](http://www.filecrunch.com/) or somewhere and PM put the link in this thread, or PM me with where I can get it.

---

### Post by jiminycricket on 2007-04-20
[http://www.zamzar.com/](http://www.zamzar.com/) Can convert docx files, it seems online

---

### Post by stuporglue on 2007-04-21
unntrlaffinity, 

Opening that file worked for me. Here are a couple of things you could check. 

1) Are you running feisty? I am. Edit: By this I meant that maybe some important library or file which is needed to work may have been upgraded between whatever older version and Feisty. 

2) Check file integrity: Can you post the md5sum of these three files: Just copy and past this if you like. It's all one line, and there are spaces after the three file names. 

```
 md5sum /usr/lib/openoffice/program/OdfConverter /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu 

```

The correct output should be

```
0255024bf53148941d9df0b0533ddbaa  /usr/lib/openoffice/program/OdfConverter
0c31809b793c597407ce7231b3750c7e  /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu
370a57074d97c013927228e273364e52  /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu

```

You could also check the openoffice.org version you have, and what openoffice.org components you have installed. These aren't all needed probably, but the openoffice.org files packages I have installed are': 

```
caroline@Elements:~$ dpkg -l | grep openoffice
ii  openoffice.org                             2.2.0-1ubuntu3                         OpenOffice.org Office suite
ii  openoffice.org-base                        2.2.0-1ubuntu3                         OpenOffice.org office suite - database
ii  openoffice.org-calc                        2.2.0-1ubuntu3                         OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      2.2.0-1ubuntu3                         OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        2.2.0-1ubuntu3                         OpenOffice.org office suite architecture dep
ii  openoffice.org-draw                        2.2.0-1ubuntu3                         OpenOffice.org office suite - drawing
ii  openoffice.org-evolution                   2.2.0-1ubuntu3                         Evolution Addressbook support for OpenOffice
ii  openoffice.org-filter-binfilter            2.2.0-1ubuntu3                         Legacy filters (e.g. StarOffice 5.2) for Ope
ii  openoffice.org-filter-mobiledev            2.2.0-1ubuntu3                         Mobile Devices Filters for OpenOffice.org
ii  openoffice.org-gnome                       2.2.0-1ubuntu3                         GNOME Integration for OpenOffice.org (VFS, G
ii  openoffice.org-gtk                         2.2.0-1ubuntu3                         GTK Integration for OpenOffice.org (Widgets,
ii  openoffice.org-help-en-us                  2.2.0-0ubuntu2                         English_american help for OpenOffice.org
ii  openoffice.org-hyphenation                 0.2                                    Hyphenation patterns for OpenOffice.org
ii  openoffice.org-impress                     2.2.0-1ubuntu3                         OpenOffice.org office suite - presentation
ii  openoffice.org-java-common                 2.2.0-1ubuntu3                         OpenOffice.org office suite Java support arc
ii  openoffice.org-kde                         2.2.0-1ubuntu3                         KDE Integration for OpenOffice.org (Widgets,
ii  openoffice.org-l10n-common                 2.2.0-0ubuntu2                         common files for OpenOffice.org language and
ii  openoffice.org-l10n-en-gb                  2.2.0-0ubuntu2                         English_british language package for OpenOff
ii  openoffice.org-l10n-en-za                  2.2.0-0ubuntu2                         English_southafrican language package for Op
ii  openoffice.org-math                        2.2.0-1ubuntu3                         OpenOffice.org office suite - equation edito
ii  openoffice.org-style-andromeda             2.2.0-1ubuntu3                         Default symbol style for OpenOffice.org
ii  openoffice.org-style-crystal               2.2.0-1ubuntu3                         Crystal symbol style for OpenOffice.org
ii  openoffice.org-style-human                 2.2.0-1ubuntu3                         Human symbol style for OpenOffice.org
ii  openoffice.org-style-industrial            2.2.0-1ubuntu3                         Industrial symbol style for OpenOffice.org
ii  openoffice.org-thesaurus-en-us             2.0.4~rc1-3ubuntu1                     English Thesaurus for OpenOffice.org
ii  openoffice.org-writer                      2.2.0-1ubuntu3                         OpenOffice.org office suite - word processor

```

(It's my wife's computer, that's why it says 'caroline@Elements') You can run "dpkg -l | grep openoffice" to get a list of your openoffice pacakges.

---

### Post by unntrlaffinity on 2007-04-21
The checksums match yours, so at least I didn't mess that up.=)

I'm using Feisty, but Xubuntu, not Ubuntu.  I do only have the bare minimum of Writer and Calc installed though.  How would I go about a complete reinstall of OpenOffice?

aptitude install openoffice.org reinstalled a lot of stuff.  But I don't have Evolution, and some of the language packages and style packages.  Also, the gnome and gtk files.  I'll try reinstalling Evolution and see if that helps.

I don't suppose anyone knows how to kill a process is Xubuntu?  I have to reboot to get rid of the OpenOffice.org load screen.

---

### Post by unntrlaffinity on 2007-04-21
I'm an idiot.  I had tried to previously install another OOo extension that was causing Writer to hang, so it really wasn't related at all to .docx.  I removed it and it's working fine now.  Thanks for the help though, it was greatly appreciated, and reinstalling is what made me remember it.

---

### Post by stuporglue on 2007-04-21
:-) It's always something little. Glad you found your problem.

---

### Post by coolclassic on 2007-04-23
I am using fiesty and I found that you don't need fakeroot. Just use the alien command:

alien -ct odf-converter-1.0.0-5.i586.rpm

It worked fine following the rest of stuporglue instructions.

---

### Post by rich.bradshaw on 2007-04-23
Yeah you can just use alien instead. You might have to apt-get that though, can't remeber if alien is installed by default...

---

### Post by techfun on 2007-05-14
Bravo!   Thanks so much for this.  It saved me running around to 30 machines running Office 2000 and installing the Office Compatibility pack.

---

### Post by msktje on 2007-05-24
I'm using ubuntu edgy. I've tried the method proposed with alien. I copied the files to the right position, but it does not work all the way. I can save to .docx and I can open the selfmade .docx but when i try to open one of the .docx files found on the internet i get a message that the file is corrupted (i've tried multiple files). Oowriter asks to restore it. When i agree with that i only got a white page. If i press no, nothing happens. I use openoffice.org 2.0.4 as you can see below. Maybe something has to be installed extra? Does anyone knows?

ii  openoffice.org                             2.0.4-0ubuntu5                       OpenOffice.org Office suite version 2.0
ii  openoffice.org-base                        2.0.4-0ubuntu5                       OpenOffice.org office suite - database
ii  openoffice.org-calc                        2.0.4-0ubuntu5                       OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      2.0.4-0ubuntu5                       OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        2.0.4-0ubuntu5                       OpenOffice.org office suite architecture dep
ii  openoffice.org-dev                         2.0.4-0ubuntu5                       OpenOffice.org SDK -- development files
ii  openoffice.org-draw                        2.0.4-0ubuntu5                       OpenOffice.org office suite - drawing
ii  openoffice.org-evolution                   2.0.4-0ubuntu5                       Evolution Addressbook support for OpenOffice
ii  openoffice.org-gnome                       2.0.4-0ubuntu5                       GNOME Integration for OpenOffice.org (VFS, G
ii  openoffice.org-gtk                         2.0.4-0ubuntu5                       GTK Integration for OpenOffice.org (Widgets,
ii  openoffice.org-help-en-us                  2.0.4-0ubuntu1                       English_american help for OpenOffice.org
ii  openoffice.org-help-nl                     2.0.4-0ubuntu1                       Dutch help for OpenOffice.org
ii  openoffice.org-impress                     2.0.4-0ubuntu5                       OpenOffice.org office suite - presentation
ii  openoffice.org-java-common                 2.0.4-0ubuntu5                       OpenOffice.org office suite Java support arc
ii  openoffice.org-l10n-common                 2.0.4-0ubuntu1                       common files for OpenOffice.org language and
ii  openoffice.org-l10n-en-gb                  2.0.4-0ubuntu1                       English_british language package for OpenOff
ii  openoffice.org-l10n-en-za                  2.0.4-0ubuntu1                       English_southafrican language package for Op
ii  openoffice.org-l10n-nl                     2.0.4-0ubuntu1                       Dutch language package for OpenOffice.org
ii  openoffice.org-math                        2.0.4-0ubuntu5                       OpenOffice.org office suite - equation edito
ii  openoffice.org-style-default               2.0.4-0ubuntu5                       Crystal symbol style for OpenOffice.org
ii  openoffice.org-style-industrial            2.0.4-0ubuntu5                       Industrial symbol style for OpenOffice.org
ii  openoffice.org-thesaurus-en-us             2.0.3-2ubuntu1                       English Thesaurus for OpenOffice.org
ii  openoffice.org-writer                      2.0.4-0ubuntu5                       OpenOffice.org office suite - word processor

---

### Post by jnewm on 2007-05-29
Thanks so much!  The instructions worked perfectly.  (PS Sorry I can't help the last poster, but following instructions is the limit of my ubuntu abilities at the moment).

---

### Post by stuporglue on 2007-05-29
msktje, 

Your version of OO.o may be too old for the plugin. I've got version 2.2.0 installed (on Feisty). I suspect that if you upgrade, it will work.

---

### Post by msktje on 2007-06-01
Thanks for the information stuporglue. I think a will wait until i can install one of the alpha's of gutsy and skip feisty. I don't need it urgent. It's something for in autumn. but according to the novel download site it should work. But i've read a lot of reviews who mentioned problems with it. So maybe the minimal requirements are set to low by novel.

---

### Post by stuporglue on 2007-06-01
> So maybe the minimal requirements are set to low by novel.

Could be. Novell may have even have enabled certain features in their older version of OO.o, which were only turned on by default in later version in other distros. 

I don't really know much about the plugin -- I just found a tutorial that worked, translated it and posted it here :-)

---

### Post by jjtechno on 2007-08-18
The conversion and install worked fine on an ooxml document that my wife recieved, it was fairly complex including .jpg's conversion. It converted ot ODF without a bit of problem. I am tempted to have her send it back to in the ODF format and see how well OOXML handles the ODF conversion. LOL!

---

### Post by Rebeca on 2007-08-29
I went through all the steps, and everything went through fine...but when I try to open a .docx file, I get an error:

> OpenOffice.org 2.2

General Error.
General input/output error.

Any ideas of what might be wrong?

I'm using feisty and openoffice 2.2.0-1ubuntu4, and I have no problems with open office. I just can't open that .docx file. I also tried using zamzar to convert it to a doc, but the .doc file zamzar sent me was garbled.

**Update:** Nevermind. There was a problem with the file itself.

---

### Post by jackocleebrown on 2007-08-29
Thanks, worked great from instructions on page 1.

Jack.

---

### Post by DarinB on 2007-09-23
Thanks Stuporglue i added the fakeroot utility and alien from synaptic and did exactly what you wrote.
workd great. 
i did not understand the part about the usr though, but i just cut and paste and it works.
thanks 
love the forums
i just choose the docx and open with ooword and then save as odt it works great.

---

### Post by PmDematagoda on 2007-09-23
Yes, .docx can be read in Open Office, thanks vnt87.

---

### Post by ram.coelho on 2007-11-03
It worked for me. I had to manually select the file type, but it went just fine.

I packed the files in an .deb. Don't know if it will work everywhere, but there it is:

[http://rapidshare.com/files/67083876/openoffice.odf-filter-openxml-1.0.deb.html](http://rapidshare.com/files/67083876/openoffice.odf-filter-openxml-1.0.deb.html)

Tested on Feisty and Gutsy (OpenOffice 2.2.0 and 2.3.0, respectively). I was not sure about minimum version of OpenOffice, so I packed it for 2.2.0 at least.

---

### Post by human on 2007-11-03
debs are also available on getdeb.net.

---

### Post by dgermann on 2007-11-18
Hi--

Just installed OOo 2.3 but I cannot open a docx file. Any suggestions?

All I get is the what filter to use box.

Do I need to copy those files mentioned? To the same directories? [edit: I tried that, but no luck. The folks over at OOoForums are saying there is no filter (yet) for OOo 2.3. See this thread: [http://www.oooforum.org/forum/viewtopic.phtml?p=263497#263497]("http://www.oooforum.org/forum/viewtopic.phtml?p=263497#263497")

Thanks!

[edited to correct the url]

---

### Post by stuporglue on 2007-11-19
[QUOTE]Just installed OOo 2.3 but I cannot open a docx file. Any suggestions?

All I get is the what filter to use box.

Do I need to copy those files mentioned? To the same directories? [edit: I tried that, but no luck. The folks over at OOoForums are saying there is no filter (yet) for OOo 2.3. See this thread: [http://www.oooforum.org/forum/viewtopic.phtml?p=26](http://www.oooforum.org/forum/viewtopic.phtml?p=26) 3438#263438[/QUOTE

dgermann, 

Did you read the post two before yours? He says: "I packed the files in an .deb. Don't know if it will work everywhere, but there it is:

[http://rapidshare.com/files/67083876...l-1.0.deb.html](http://rapidshare.com/files/67083876...l-1.0.deb.html)

Tested on Feisty and Gutsy (OpenOffice 2.2.0 and 2.3.0, respectively). "

So, yes you need to install something else, and according to ram.coelho they were tested with 2.3.0. I'm not sure what the OOo Forums folks were saying because the link you gave didn't work. 

Try downloading the linked files ram.coelho listed two posts above yours and see if that isn't easier than the install instructions on the first page of this topic. 

-- Stuporglue

---

### Post by avik on 2007-11-19
Anyone know if this works on 64bit Gutsy?  The Novell download says i586, and GetDeb only has up to Fiesty 64 bit.

---

### Post by dgermann on 2007-11-19
stuporglue--

OK, tried that download and the auto install did not work. So I tried this and got this--

```
 sudo dpkg -i openoffice.odf-filter-openxml-1.0.deb
Password:
Selecting previously deselected package openoffice.org-filter-openxml.
(Reading database ... 165412 files and directories currently installed.)
Unpacking openoffice.org-filter-openxml (from openoffice.odf-filter-openxml-1.0.deb) ...
dpkg: dependency problems prevent configuration of openoffice.org-filter-openxml:
 openoffice.org-filter-openxml depends on openoffice.org (>= 2.2.0); however:
  Package openoffice.org is not installed.
dpkg: error processing openoffice.org-filter-openxml (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-filter-openxml
```

I do have OOo 2.3 installed so it looks like it is looking in the wrong place for the dependency. Any suggestions?

Thanks!

---

### Post by shane2peru on 2007-11-20
I'm using Gutsy (up to date) and I installed the OpenOffice.org from their website 2.3.0(the deb) and it doesn't work for me.  :(  I also installed the deb from getdeb.net for the converter.  No go here.  Any ideas would be appreciated.  No, I'm not going to uninstall my OO.o and install the Ubuntu package.  Other options or ideas would be appreciated.  :)

Shane

---

### Post by lordawesome on 2007-11-21
My docx files didn't open at first. I confirmed all files were copied into the right directories and everything was there. I changed the properties for the docx files to open with open office writer, and it worked. However, some of the formatting of the files was not correctly rendered (underlines where they shouldn't be, Image size, font, etc). At least I can open them though. Thanks

---

### Post by dgermann on 2007-11-21
lordawesome--

That's good news for you, but so far not for me.

I did what you said, and still get the "select filter" screen in OOo.

I am running Ubuntu 6.06LTS (Dapper), OOO 2.3 (from the OOo site, not from Novell or any other third party provider).

lordawesome, what are you running?

Anybody have any suggestions?

---

### Post by shane2peru on 2007-11-21
> **dgermann said:**
> lordawesome--

That's good news for you, but so far not for me.

I did what you said, and still get the "select filter" screen in OOo.

I am running Ubuntu 6.06LTS (Dapper), OOO 2.3 (from the OOo site, not from Novell or any other third party provider).

lordawesome, what are you running?

Anybody have any suggestions?

I'm in the same boat as you.  It would be nice if someone had an answer.

Shane

---

### Post by dgermann on 2007-11-22
shane2peru--

Last night I upgraded my system76 from 7.04 to 7.10. It loaded OOo 2.3, and out of the box it was able to open and read docx. It does not seem to have a way to save as docx.

---

### Post by shane2peru on 2007-11-24
> **dgermann said:**
> shane2peru--

Last night I upgraded my system76 from 7.04 to 7.10. It loaded OOo 2.3, and out of the box it was able to open and read docx. It does not seem to have a way to save as docx.

Ok, I reinstalled OO.o with the Ubuntu version and it works now.  Thanks.

Shane

---

### Post by dgermann on 2007-11-24
Shane--

Can you also save as docx, or just read?

---

### Post by shane2peru on 2007-11-24
> **dgermann said:**
> Shane--

Can you also save as docx, or just read?

I can save them as docx only if I open up a docx.  However if I just open a document and choose save as, it doesn't have the docx option that I saw.  

Shane

---

### Post by dgermann on 2007-11-25
Shane--

OIC! If you save the same file it saves to docx.

But if you do a save as, there is no choice for docx. I think I saw that part of the equation and will have to see about editing and saving back to the docx file.

Thanks!

---

### Post by shane2peru on 2007-11-25
> **dgermann said:**
> Shane--

OIC! If you save the same file it saves to docx.

But if you do a save as, there is no choice for docx. I think I saw that part of the equation and will have to see about editing and saving back to the docx file.

Thanks!

This is kind of a hack, but if you open a docx file and then just erase everything and write what you want, you can have a docx file too.  However, I don't know what the point of that would be, I'm not really into using Microsoft's formats.  However if it must be done for work or something it could be done.

Shane

---

### Post by dgermann on 2007-11-25
Shane--

Ahh! So you can probably rename the file too.

Just tried that and it would not open it. (I just renamed it in nautilus.) Also tried copying a couple other ways, such as a command line copy, and even changing its permissions.

Success! I had to log in to the samba server on which this file lives; then I copied it using cp -p.

Long way around the barn. I sure hope the next version of OOo has this figured out and seamless.

---

### Post by 1337455 10534 on 2007-11-27
OFFICIALLY WORKING FOR THE LATEST VERSION OF GUTSY!! YAY!!
Is there anyway to tell gconf to open docx packages with OO by default?

---

### Post by dgermann on 2007-11-27
1337455 10534--

Will this do what you want?

From Nautilus, right click on the docx file, choose Properties> Open With and there select OOo2.3.

---

### Post by shafin on 2007-12-04
have you tried this?
[http://www.getdeb.net/search.php?search_distro_id=6&keywords=openxml](http://www.getdeb.net/search.php?search_distro_id=6&keywords=openxml)

---

### Post by dgermann on 2007-12-04
shafin--

It looks like something from a couple of other sites. I have downloaded and installed one of them and it was no go.

Thanks!

---

### Post by nitinag on 2008-02-28
Try this [http://nitinsthoughts.wordpress.com/2008/02/28/docx-for-open-office/]("http://nitinsthoughts.wordpress.com/2008/02/28/docx-for-open-office/")

--Nitin

---

### Post by karldiechmann on 2008-04-25
In Ubuntu Gutsy, Stuporglue's instructions should also work if you use alien to create a debian package, then unpack it with gdebi:
```

$ sudo alien odf-converter*.rpm
$ sudo gdebi odf-converter*.deb
```

After running those commands, my installation of OOffice was able to read docx just fine.

---

### Post by svaens on 2008-07-23
hi guys, 

I just had this same problem..... and out of principle didn't want to stoop to downloading a converter for this shame of an open standards format. 

The way to read those few docx you find (when you must) is this:

1. post the link to the doc in the google search
2. usually, only that link will appear in the search results, 
3. it will appear with a 'view as html' option. 
4. click, and view in open HTML

have fun!

** of course, this depends on you having found it online.. **

---

