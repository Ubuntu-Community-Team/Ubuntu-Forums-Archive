---
title: "Is There any MS office 2007 extension for Open office??"
date: 2007-07-23
forum: General Help
---

### Post by arashiko28 on 2007-07-23
I have been thinking about eraing for good my windows HDD, how ever, one thing stops me. University. People has already bought Vista an MS Office 2007 and we have a large quantity of presentations in class, the thing is that my partners and teachers are giving theirs in .pptx, docx which are office 2007 extensions, I had my hopes into that the new version of open office would have that covered, but not yet. Can somebody give me an altermative. Oh! and office 2007 won't install on ubuntu. It cancels it self the installation using wine.

---

### Post by Voynix on 2007-07-23
Hi, 

have a look at this [thread.]("http://ubuntuforums.org/showthread.php?t=386385") There is a docx converter from [novell]("http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58%7E"). I am not sure about the other *.x office formats. These are the steps:

1. Download the docx translator: [http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58%7E](http://download.novell.com/SummaryFree.jsp?buildid=ESrjfdE4U58%7E)
2. Using alien, convert the rpm into a debian package
    sudo alien -d odf-converter-1.0.0-5.i586.rpm
3. Install the deb file
4. Copy the file **OdfConverter** from  /usr/lib/ooo-2.0/program/ to /usr/lib/openoffice/program/
5. Copy the file **MOOXFilter_cpp.xcu** from /usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Filter to /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/
6. Copy the file **MOOXTypeDetection.xcu** from /usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Types to 
/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/

Cheers

---

### Post by MrFSL on 2007-07-23
I hate to troll but sometimes I cannot resist

Micro$oft Office is (IMHO) the greatest hinderer to Open Source Software and Linux that there is. The dependency on this Office suite is sickening! 

(Sorry... my company just made the managerial decision to employ a Micro$oft Sharepoint server which I am forced to "manage" and its making me want to kill everything!

:(

---

### Post by Voynix on 2007-07-23
> **MrFSL said:**
> I hate to troll but sometimes I cannot resist

Micro$oft Office is (IMHO) the greatest hinderer to Open Source Software and Linux that there is. The dependency on this Office suite is sickening! 

(Sorry... my company just made the managerial decision to employ a Micro$oft Sharepoint server which I am forced to "manage" and its making me want to kill everything!

:(

I agree... what is more sickening is to be sent docx files because the users are too lazy to save the documents in compatible formats. I receive files every day in word perfect, works, odt, docx and doc formats!

---

### Post by arashiko28 on 2007-07-25
> **MrFSL said:**
> I hate to troll but sometimes I cannot resist

Micro$oft Office is (IMHO) the greatest hinderer to Open Source Software and Linux that there is. The dependency on this Office suite is sickening! 

(Sorry... my company just made the managerial decision to employ a Micro$oft Sharepoint server which I am forced to "manage" and its making me want to kill everything!

:(

This actually does make me sick, but if i don't do this, I'll be the one to blame, because  "the gave it to me" and i'm supposed to do the rest.... but, revenge it's sweet, i'll pass them in .odt, to see what they do.:lolflag:

Voynix, this web page says that it's only for SUSE :s I have ubuntu...

---

### Post by eentonig on 2007-07-25
> **Voynix said:**
> I agree... what is more sickening is to be sent docx files because the users are too lazy to save the documents in compatible formats. I receive files every day in word perfect, works, odt, docx and doc formats!

I actually always sent them back, saying that I can't open those files (even though I can) and ask them to sent me an 'Open' format or an older ms version.

Nobody ever complains.

---

### Post by LaRoza on 2007-07-25
I am in school, and have spread OpenOffice.org around, it is used much by users here, but not in school, only at home.

---

### Post by arashiko28 on 2007-07-25
I managed to install alien and make the .deb and installed it, but i cant copy the files, it says that i have no permition to do it. i'm the only user, how do i do this?:confused:

---

### Post by Voynix on 2007-07-25
> **arashiko28 said:**
> I managed to install alien and make the .deb and installed it, but i cant copy the files, it says that i have no permition to do it. i'm the only user, how do i do this?:confused:

You need admin rights to copy the files. 

```
sudo cp /usr/lib/ooo-2.0/program/OdfConverter /usr/lib/openoffice/program/
sudo cp /usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/
sudo cp /usr/lib/ooo-2.0/share/registry/modules/org/openoffice/TypeDetection/Types/MOOXTypeDetection.xcu /usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Types/
```

---

### Post by Voynix on 2007-07-25
> **LaRoza said:**
> I am in school, and have spread OpenOffice.org around, it is used much by users here, but not in school, only at home.

My university has office 2003 and favours all microsoft document formats. Our internet and intranet heavily rely on microsoft active x, and most of the features can only be accessed through internet explorer and windows. Until very recently it was even impossible to open .odt files until I came across the portable open office which I use daily. 

Honestly, such a waste of money and resources to discriminate and impose proprietary formats and systems on students, staff and visitors. A real shame. 

I wish I could use the ubuntu live CD at work, but system admins have password protected the bios...

---

### Post by arashiko28 on 2007-07-27
Depending on Microsoft x??? Dude I bet you have most of the time with the system down and no signal than actually working time. It's the same in my university, the server even messed up my class selection and they now have to fix it manually.

On the other hand, this is only for word... i need most ppt...:(

---

### Post by vexorian on 2007-07-27
Yes, use the translator developed by  MSLinux , should work.

--
Also, had to be done:

---

### Post by Depressed Man on 2007-07-27
> **arashiko28 said:**
> Depending on Microsoft x??? Dude I bet you have most of the time with the system down and no signal than actually working time. It's the same in my university, the server even messed up my class selection and they now have to fix it manually.

On the other hand, this is only for word... i need most ppt...:(

Haha that reminds me of the time one of the classes I had (which relies on computers for every student that's built into the desk) at Maryland. It was updating (for some reason the update didn't happen overnight like it was suppose to). So when we came into class on midterm day we were treated to the CLI windows showing the progress of the system wide update.

All the computers in the Plant Life Sciences building was down that day lol.

---

### Post by ManFromMars on 2007-08-09
Ugh, new MSOffice formats, great. There was a back page article in Linux Format about this issue actually - someone's laptop had come pre-installed with a trial of MSOffice 07, which ONLY allows you to save .docx etc. file types, and then expires after 30 days, so if you save any important work you're obliged to continue using MSOffice 07 unless you want to do some tinkering (and the average user obviously doesn't). My (former) university used MSOffice mostly, though fortunately my supervisor/AI module lecturer refused to accept any work in .doc format, which was nice :-D

---

### Post by javroch on 2008-03-30
I'm not exactly sure why nobody else seems to have tried this, but if you download the odf-converter-x.x-x.oxt file from Novell's website, instead of the rpm, you can install it just as you would in Windows. AND, it will not only allow you to use .docx files it'll also do .xlsx and .pptx files as well. I'll outline the steps for you if you'd like:

Go to Applications > Office and open OpenOffice.org Word Processor
In OpenOffice.org Word Processor go to Tools > Extension Manager...
In Extension Manager click "Add..." and locate the .oxt file.

That's it!

---

### Post by chilinski on 2008-03-30
I don't recall if I saw this on this forum or on the OpenOffice forum.

If you save the .docx file to your computer, then right click on it and tell it to open with OpenOffice Writer, it will open the file. I'm sure it loses some formatting, but at least you can read the thing...in most cases that's enough.

---

### Post by calc on 2008-03-31
Also the Ubuntu version of OpenOffice in 7.10 and 8.04 already supports MS Office 2007 format at least to some extent. If you can't open a particular file by double clicking on it in the file manager it may still open via OpenOffice File->Open since not all of the Office 2007 file types have proper mime type setup in Ubuntu. Some of this already works but it may not be fully supported until Ubuntu 8.10 due to needing proper names for the mime-types in shared-mime-info.

---

