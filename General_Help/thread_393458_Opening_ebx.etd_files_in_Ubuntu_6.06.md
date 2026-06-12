---
title: "Opening ebx.etd files in Ubuntu 6.06"
date: 2007-03-25
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-03-25
I'm trying to open e-book files from an online college with Ubuntu. I have Adobe installed but it is still not able to open the files. Is there a workaround for this?

---

### Post by MrSweet on 2007-04-29
I am in the same boat right now.  I have acrobat reader installed from Automatix2 and I am unable to open this file, or find another way of just getting the .pdf.

After some looking around I noticed that in my /home/<user>/.mozilla/plugins directory there is no acrobat plugin there.  I am currently doing a search to see where it ended up.  I hope it is a matter of putting a sym-link to fix this, but I am not sure.

Mr. Sweet

---

### Post by MrSweet on 2007-05-06
I was able to find a little bit of information about this topic.  I used my laptop with Windows XP to grab the PDF files from my schools site.  I have Adobe Reader 7 on that system.  Once I clicked the link it did launch the Reader and then grabbed the page, but only after it did some type of verification.  After I got the PDF downloaded I moved it to my Ubuntu machine.  I tried to open it with acroread but I got an error saying that I was missing a plugin.  I compared the two plugin lists and noticed that the Ubuntu machine did not have a plugin called AdobeDRM.  I did a search and found that you can get the plugin from the Adobe site after you use a .Net Passport for verification.  I did not go through the whole process because I do not know if this would let me use the e-books from my shcool.  I think that the site where I got the PDF file has it's own verification so I don't think that would help me.

I am not sure at this point how to get verified on my Ubuntu machine so that I can read the e-books here.  Right now I am stuck using Windows to read the text, unless I want to print off 150 pages. At that point I am better off just buying the book.

Hope this lends a little insight.  I also hope that there is more then 2 people interested in this subject.  I think DRM is going to be an problem that only gets worse in the future, so I hope more people take an interest in this and we can figure out a good solution for the future.

Mr. Sweet

---

### Post by JawsThemeSwimming428 on 2007-05-07
I have been trying to fix the problem as well, but to no avail. At this point I am not quite sure what to do, but I do not think there is a known fix. I do have a Windows XP machine but I try not to use it at all. I use a Thin Client and RDP to my Windows XP box at work and open the PDF in the RDP session. I try to avoid turning the XP box at my house on at all costs!!! Nothing but problems. Try to keep us posted!

---

### Post by muppetmuffin on 2008-03-09
See:
[http://www.linuxquestions.org/questions/showthread.php?p=2973149#post2973149](http://www.linuxquestions.org/questions/showthread.php?p=2973149#post2973149)

If you don't want to navigate adobe's awful flash homepage, the download link for adobe is:
[http://www.adobe.com/products/acrobat/readstep2_servefile.html?](http://www.adobe.com/products/acrobat/readstep2_servefile.html?)

I'm in the same situation with the university digital library subscription. I just tried Adobe 8 under wine but didn't get past installation. I'm installing 7 at the moment and already have cups-pdf (for my online physics textbook which I can't print from Linux and need win inside virtualbox for, if I want to be able to read the "printed" sections of using evince :( ...).

Okay well I can't get the registration down. Maybe its because I'm using different names and emails for different signups. It's really a pain in the butt, but maybe there is hope to getting it working. Or I could just wait for the paper copy of the book I want to get into the library or if I'm really impatient see what the wet 'n wild web has to offer. If I'm really patient, I suppose I could just wait for the moronic, absolutely infeasible idea of digital restrictions management to blow over and information to finally be free... sike.

Peace.

---

### Post by a30d on 2008-04-11
I am currently running Gutsy and have been able to get around the whole Adobe DRM issue using Wine.

First, I downloaded and installed the latest version found of Wine found in the repository.

Second, I downloaded ies4linux to install IE 6.0 in Wine.

Third, I download Adobe Acrobat Reader 7.0.9 for WinXP from [www.adobe.com](www.adobe.com). Firefox automatically ran the file through Wine and the install was successful.

Fourth, I went through IE 6.0 to [http://aractivate.adobe.com](http://aractivate.adobe.com), signed in using my Passport identification, and requested to install on a new computer. I followed the steps, and eventually it asked me to download a file with extension ".edn". I saved this to my user directory then exited IE 6.0.

Fifth, I opened Adobe Acrobat Reader 7.0.9, via Wine, and opened the ".edn" file I saved in the previous step. Adobe Acrobat Reader then goes through the process and verifies all the credentials. Make sure you have a working internet connection!

My online university provides the course E-Books using DRM PDF files. The whole process is initiated through an "ebx.etd" file (which looks just like an XML file) which Adobe Acrobat Reader uses to verify your identity. I download this ".etd" file, using any browser, and save it to the home directory. Then, through Adobe Acrobat Reader via Wine, I can open this file and the PDF file with DRM will be downloaded and viewed anytime you wish.

Hope this helps!
-Bryan Allred

---

### Post by electrosoccertux on 2008-05-12
> **a30d said:**
> I am currently running Gutsy and have been able to get around the whole Adobe DRM issue using Wine.

First, I downloaded and installed the latest version found of Wine found in the repository.

Second, I downloaded ies4linux to install IE 6.0 in Wine.

Third, I download Adobe Acrobat Reader 7.0.9 for WinXP from [www.adobe.com](www.adobe.com). Firefox automatically ran the file through Wine and the install was successful.

Fourth, I went through IE 6.0 to [http://aractivate.adobe.com](http://aractivate.adobe.com), signed in using my Passport identification, and requested to install on a new computer. I followed the steps, and eventually it asked me to download a file with extension ".edn". I saved this to my user directory then exited IE 6.0.

Fifth, I opened Adobe Acrobat Reader 7.0.9, via Wine, and opened the ".edn" file I saved in the previous step. Adobe Acrobat Reader then goes through the process and verifies all the credentials. Make sure you have a working internet connection!

My online university provides the course E-Books using DRM PDF files. The whole process is initiated through an "ebx.etd" file (which looks just like an XML file) which Adobe Acrobat Reader uses to verify your identity. I download this ".etd" file, using any browser, and save it to the home directory. Then, through Adobe Acrobat Reader via Wine, I can open this file and the PDF file with DRM will be downloaded and viewed anytime you wish.

Hope this helps!
-Bryan Allred

This does not work for me...
I get an activation error (client code 3). :(

---

