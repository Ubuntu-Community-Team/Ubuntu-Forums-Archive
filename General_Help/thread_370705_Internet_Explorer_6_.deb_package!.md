---
title: "Internet Explorer 6 .deb package!"
date: 2007-02-26
forum: General Help
---

### Post by mhancoc7 on 2007-02-26
I am working on a project to build a new GUI program installer for wine. This has been done, but I just wanted to see what I could put together. You can check it out at the thread below.
[http://www.ubuntuforums.org/showthread.php?t=369671](http://www.ubuntuforums.org/showthread.php?t=369671)

During the process of building the GUI for wine I started looing into what programs it would install using wine. Internet Explorer was an obvious choice since it is a very commonly used program.

Long story short, I build a .deb package that will install Internet Explorer. I have only tested this on my personal system. I would appreciate anyone who would be willing to test it for me. It will not make any changes to your current wine configuration. If you decide to test it please remember like any other "beta" software you should USE AT YOUR OWN RISK.

Please let me know how it works for you if you do use it.
You can download the latest version below.
**Edgy:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)
**Dapper:**
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-dapper.html)

[B][I]Edit: v1.1 works with the Ubuntu CE web content filtering!

Edit: I have removed the package for further review. Some people have raised concerns about the legality of the package.[/I][/B]

[I][B]Edit: Ok, v1.2 is now ready. I have completely rewritten the app. It is now basically a front-end for ies4linux. It simplifies things a bit though. It has a nice GUI that takes the fear of the terminal window away. :) It also alerts when there is an error with any of the CAB files and cleans up so the user can try again. This is a common problem with ies4linux. The IEs 4 Linux Installer menu icon is replaced with the Internet Explorer icon after setup is complete. No Desktop icon by default.

Edit: Added alerts to v1.3 to remind Ubuntu CE users to disable dansguardian before running IEs 4 Linux Installer. I also added a "Successful Installation" alert.

[/B][/I][I][B] Edit: v1.4 now preserves the downloaded components if the install fails due to a download error. This means that the next time you run the IEs 4 Linux installer you will only need to download the files that were not downloaded the first time.

Edit v1.5 released. Added an alert for Ubuntu CE users due to parental control concerns.

[/B][/I]  Thanks, Jereme

---

### Post by ~LoKe on 2007-02-26
Worked for me, unfortunately.

---

### Post by Maestro23 on 2007-02-26
> **~LoKe said:**
> Worked for me, unfortunately.

Too funny.:)

---

### Post by mhancoc7 on 2007-02-26
> **~LoKe said:**
> Worked for me, unfortunately.

I am glad that it worked, but I am not sure if I get the joke.

I am not a big fan of Internet Explorer. I only use it to test my webpages.

Jereme

---

### Post by yota on 2007-02-26
Worked for me.

Really handy, since sometimes I need to use ie6-only crappy webapps.

Thanks!

---

### Post by chrome307 on 2007-02-26
I downloaded this to my desktop and tried to install it .......... no luck :(

[IMG]http://1pix.org/out.php/i549_Untitled.png[/IMG]

---

### Post by AlanRogers on 2007-02-26
I think that you need to right-click on the DEB file, choose properties and set it to be executable. Alternatively, try running it from a Terminal with Sudo.

---

### Post by chrome307 on 2007-02-26
I've downloaded it again onto my desktop and changed the permissions as suggested ... with no luck :(

[IMG]http://i17.tinypic.com/2v0dbls.png[/IMG]

How do I get it run in the terminal ?

```


sudo /home/optiplex/Desktop/internet-explorer-6-ubuntu_1.1_all.deb


```

---

### Post by Ramses de Norre on 2007-02-26
```
sudo dpkg -i  /home/optiplex/Desktop/internet-explorer-6-ubuntu_1.1_all.deb
```

---

### Post by mhancoc7 on 2007-02-26
> **chrome307 said:**
> I downloaded this to my desktop and tried to install it .......... no luck :(

[IMG]http://1pix.org/out.php/i549_Untitled.png[/IMG]

> **chrome307 said:**
> I've downloaded it again onto my desktop and changed the permissions as suggested ... with no luck :(

[IMG]http://i17.tinypic.com/2v0dbls.png[/IMG]

How do I get it run in the terminal ?

```


sudo /home/optiplex/Desktop/internet-explorer-6-ubuntu_1.1_all.deb


```

No need to change the permissions. It appears that my upload was corrupted. I will upload it again and post when I am sure that it is correct. Sorry about that. I really need a better connection! :)

Jereme

---

### Post by mhancoc7 on 2007-02-26
Ok the deb should be fixed now. See OP.
Thanks, Jereme

---

### Post by polki@mac.com on 2007-02-27
Worked like a charm. Huge thanks. Now my wife can check her work webbmail. Yes, they are forcing people to use IE...
Again, thanks!

---

### Post by ~LoKe on 2007-02-27
Anything particularly wrong with the IE tab extension?

---

### Post by bodycoach2 on 2007-02-27
Worked for me! Quick as a breeze. Now I can do my Sam's courses for school! Thanks.

---

### Post by Sammi on 2007-02-27
Wow I didn't expect IE to be a 73 MB download. Just how much bloat is in there?

To compare Firefox is 9.2 MB and Opera is only 5.5 MB :shock:

---

### Post by r4ik on 2007-02-27
Anybody confirm a file size of 73MB please ?
Thanks.

---

### Post by r4ik on 2007-02-27
> **Sammi said:**
> Wow I didn't expect IE to be a 73 MB download. Just how much bloat is in there?

To compare Firefox is 9.2 MB and Opera is only 5.5 MB :shock:

Thank you Sammi.  :)

---

### Post by wxnker on 2007-02-27
This is so great. Thank you very much for this deb package.

I do not use Internet Explorer for web browsing but most poker software AND "instant play" clients need IE. Now I can access the two sites I like the most (Ladbrokes and 32RedPoker) from the "instant play" client and do the few things that do not work yet with the "download version" and Wine. This is mainly banking options. It's kinda nice to be able to see how much money is in the account. :-D

I have been trying to install IE 6 for some time with Winetools etc. but I always got a lot of bugs. Also IE4Linux was not working good enough for me to work with pokersites.

This deb works out of the box. I just went to the adobe site and installed "Schockwave" and "authorware" with no problems at all, and everything works.

TY so much :KS

---

### Post by Sammi on 2007-02-27
I tried installing Java from [www.java.com](www.java.com), but that didn't work :(

---

### Post by chriswyatt on 2007-02-27
> **~LoKe said:**
> Anything particularly wrong with the IE tab extension?

Are you sure this would actually work on Linux?  I'm quite sure IE tab just embeds Internet Explorer in Firefox, rather than emulating it.

---

### Post by mhancoc7 on 2007-02-27
> **~LoKe said:**
> Anything particularly wrong with the IE tab extension?

The IE tab only works with Windows, AFAIK.

Thanks to all who have given feedback. It really helps for me to get things working. I am glad that you are enjoying it.

Jereme

---

### Post by r4ik on 2007-02-27
Debian Etch asked for my rootpasswrd and then bounced it back to me invalid.
Which was enough for me to delete it again.
Just does not work for me .
No big deal.

---

### Post by mhancoc7 on 2007-02-27
> **r4ik said:**
> Debian Etch asked for my rootpasswrd and then bounced it back to me invalid.
Which was enough for me to delete it again.
Just does not work for me .
No big deal.

Thanks for letting me know. I have only tested it on Ubuntu so it is nice to hear what happens on Debian.

Jereme

---

### Post by rambo_050575 on 2007-02-27
Thank you,

You can't image how much this means to me. I could not get wine to work :-?  And I Have to have IE 5.5 or better to use my employers  web site. With out it I would not get payed you saved me hours at the library. 

Internet Explorer 6 .deb package runs a lot slower than Firefox on my old PC but works good.

thank you,

Adam Nelson :lolflag:

BTY I use Ububtu6.10/Kububtu

---

### Post by mhancoc7 on 2007-02-27
> **rambo_050575 said:**
> Thank you,

You can't image how much this means to me. I could not get wine to work :-?  And I Have to have IE 5.5 or better to use my employers  web site. With out it I would not get payed you saved me hours at the library. 

Internet Explorer 6 .deb package runs a lot slower than Firefox on my old PC but works good.

thank you,

Adam Nelson :lolflag:

BTY I use Ububtu6.10/Kububtu

Awesome!! I am very glad to hear that you found it useful.

Jereme

---

### Post by mhancoc7 on 2007-02-27
> **rambo_050575 said:**
> Thank you,

You can't image how much this means to me. I could not get wine to work :-?  And I Have to have IE 5.5 or better to use my employers  web site. With out it I would not get payed you saved me hours at the library. 

Internet Explorer 6 .deb package runs a lot slower than Firefox on my old PC but works good.

thank you,

Adam Nelson :lolflag:

BTY I use Ububtu6.10/Kububtu

Awesome!! I am very glad to hear that you found it useful.

Jereme

---

### Post by Cloudy on 2007-02-27
Worked like a charm for me. No problems installing it, no problems using it. Thanks for this.

---

### Post by HasratUSA on 2007-02-28
Congratulations. You have written/created a great useful tool for those who can't do without IE, or any software developed by MS. I hope in future you would do more to help those in need who have just switched to Linux but still wants to use 'this and that' from their previous OS.

However, even when I was in complete dark about Linux and Ubuntu and had to resort to Windows XP to perform my daily tasks,  I never really liked any version of IE. 

First of all it has plenty of security problems and users are virtually forced to download additional malware, spyware, trojanware and blah blah blah ware _______ (fill in the blanks please) checker/scanner/remover/killer/repairer and blah blah blah (to name a few, i would say spybot search and destroy, adaware, spy doctor, spy killer etc) to keep IE and their computers safe. 

Secondly, it has been the target of numerous attacks by so many hackers scattered all over the globe that some security experts say that without running a reliable firewall nobody should even visit [www.yahoo.com](www.yahoo.com) using IE. IE is a smelly nest which is full of basically all kinds of vulnerabilities and weak code structure and no matter how hard Microsoft tries to fix the glitches, it would never really be as safe as normal users want it to be.

Thirdly, IE is an internet browser that's meant to be run only on one operating system, which is Windows, while Netscape, Mozilla and other browsers have different versions for different OSs. When I bought this computer, i found out IE with the OS. I needed the OS to operate the computer, but i didn't want a security hazard to be shipped with it. I wasn't even able to uninstall it. So, all in all, it seemed to me that someone was playing monopoly somewhere.

You should be proud that you have made an useful 'thingy' for the folks here, no doubt,  though

---

### Post by xenoalien on 2007-02-28
Yeah, IE has very poor security... can you tweak the IE 6 deb file to be more secure? I can see why IE would be good because some programs installed by wine require IE to work.

Try making a IE 7 deb file. It would be a bit more secure.

BTW IE installed like a charm. Good job!

---

### Post by nixternal on 2007-02-28
You do realize that you are in fact breaking the law?  First of all did the evil empire give you permission to do this? If so is that agreement in the package? Is there a EULA?  No matter how useful this application is to the masses, I don't feel for one that it is legal and two goes against everything the Ubuntu and Linux communities try to follow. Oh well, who am I to say though. Run lintian -i *.dsc before you pbuild it next time and take care of some of the packaging issues at least.

---

### Post by aysiu on 2007-02-28
> **nixternal said:**
> You do realize that you are in fact breaking the law?  First of all did the evil empire give you permission to do this? If so is that agreement in the package? Is there a EULA?  No matter how useful this application is to the masses, I don't feel for one that it is legal and two goes against everything the Ubuntu and Linux communities try to follow. Oh well, who am I to say though. Run lintian -i *.dsc before you pbuild it next time and take care of some of the packaging issues at least.
Read this:
[http://www.tatanka.com.br/ies4linux/page/Legal_notices](http://www.tatanka.com.br/ies4linux/page/Legal_notices)

---

### Post by nixternal on 2007-02-28
> *    Subject to the distribution requirements described below, if you 
obtain the OS Components on a CD-ROM from Microsoft, you may redistribute 
sp5i386.exe, sp5alpha.exe, sp5symi.exe and sp5syma.exe separately or together 
(collectively "Redistributable Code").  You must verify that you are 
distributing the most recent version of the Redistributable Code.  Check the 
Microsoft FTP server at 
[ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/](ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/) for the latest 
version.  If you find a more recent version of the Microsoft FTP server, you 
may download such files for your own use; provided, however, you may not 
redistribute any such files without first obtaining them on a CD-ROM from 
Microsoft.

DISTRIBUTION REQUIRMENTS:  Microsoft grants you the non-exclusive, worldwide, 
royalty free, right and license to reproduce and distribute an unlimited 
number of copies of the Redistributable Code either for use in conjunction 
with your computer hardware product or with your own software product, 
designed to operate in conjunction with Microsoft Windows NT, provided: 
(a) each copy of the Redistributable Code is a true and complete copy made 
directly from the Microsoft CD-ROM; 
(b) you require any installation of the Redistributable Code to be made by 
running the self-extracting executable file or files; 
(c) you distribute the readme.txt file and \drvlib directory along with and in 
the same directory as any individual or group of Redistributable Code you 
distribute; 
(d) you distribute your own software product containing the Redistributable 
Code on a CD-ROM and pursuant to an End-User License Agreement with terms no 
less protective than those contained in the applicable OS Product EULA.  Your 
End-User License Agreement may be "break-the-seal", "click-wrap" or signed; 
(e) you include all copyright and trademark notices contained in the 
Redistributable Code; 
(f) you do not distribute the Redistributable Code for profit; 
(g) you do not modify the Redistributable Code; and 
(h) you do not permit further redistribution of the Redistributable Code.

Export Restrictions.

You agree that you will not export or re-export the OS Componenets to any 
country, person, or entity subject to U.S. export restrictions. You 
specifically agree not to export or re-export the OS Components: 
(i) to any country to which the U.S. has embargoed or restricted the export of 
goods or services, which as of March 1999 include, but are not necessarily 
limited to Cuba, Iran, Iraq, Libya, North Korea, Sudan and Syria, or to any 
national of any such country, wherever located, who intends to transmit or 
transport the OS Components back to such country; 
(ii) to any person or entity who you know or have reason to know will utilize 
the OS Components or portion thereof in the design, development or production 
of nuclear, chemical or biological weapons; or 
(iii) to any person or entity who has been prohibited from participating in 
U.S. export transactions by any federal agency of the U.S. government. You 
warrant and represent that neither the BXA nor any other U.S. federal agency 
has suspended, revoked or denied your export privileges. For additional 
information see [http://www.microsoft.com/exporting/](http://www.microsoft.com/exporting/).[FONT=verdana,geneva,lucida,'lucida grande',arial,helvetica,sans-serif]
[/font][http://www.microsoft.com/msdownload/ieplatform/ie/license.txt](http://www.microsoft.com/msdownload/ieplatform/ie/license.txt)

According to this, it is in fact illegal distributing it the way it is being distributed here. Plus the export regulations in fact come into play in this instance as well.

---

### Post by Bloch on 2007-02-28
> You do realize that you are in fact breaking the law? First of all did the evil empire give you permission to do this? If so is that agreement in the package? Is there a EULA? No matter how useful this application is to the masses, I don't feel for one that it is legal

The only reasonable purpose of IE explorer for Linux, and the only reason I have it, is to check that the web pages I create will look fine on MS windows with IE6.

If something very useful and harmless infringes a law which no-one will bother to enforce, does that justify infringing that law?

Yes.

And when you play your DVD and mp3s and wmv streaming video, are all your licences in order?

---

### Post by aysiu on 2007-02-28
I'm not a lawyer and don't speak legalese.

Can you translate into plain English line for line what parts of the EULA you think are violated by this .deb?

The only thing I could find about the legality of it from an interpretative standpoint is this article:
[IE For Linux?](http://www.internetnews.com/dev-news/article.php/3629786)

[quote=the article]But is IEs 4 Linux legal?

Lopes said that he has never been contacted by Microsoft or one of its representatives about the project.

"I think IEs 4 Linux is not a problem for them, it is too small," Lopes said. "I have some legal notices on IEs4Linux website since I released the first version, to advise users to not make anything illegal."

According to the disclaimer posted on the IEs 4 Linux Web site by Lopes, "IEs 4 Linux is free software, open source, covered by GPL. But IE is proprietary, copyrighted, and you have to accept their license." He goes on to state that in order to install any Microsoft program included on IEs 4 Linux, the user needs a valid Windows license.

"IEs4Linux will not ask for it and you can run everything without any problem even if you don't have a license. But it is illegal and a I have not to do with this."

Internetnews.com contacted Microsoft for this story, but a spokesperson was not immediately available for comment. [/quote]

---

### Post by nixternal on 2007-02-28
For one the packaging doesn't contain the necessary license files. Second the redistribution is also illegal, as well as in the terms of the import/export of it.

Back when I worked for AT&T, when we packaged any of the IEs we had to pay 1) a redistribution fee, 2) signed an agreement that we wouldn't provide the package to residents outside of the continental US, as well as other items. All of our packages contained the proper licensing information and a EULA that the end user had to agree to prior to installing.

I don't care that you use this for test website development as I think it is useful in such cases. Granted more than likely the only thing MS would do is send a cease and desist order. Heck, Microsoft has made it damn near impossible for Linux documenters to even screenshot or write about MS products w/o the proper licensing.

As for having my stuff in order when using wmv and such, well I don't. Why? Because I don't play DVDs on my computers, that is what my TV is for, I don't have, nor find the use for, wmv files. I don't have mp3 files only ogg files. I have in fact went against these rules and regulations in the past, though it is wrong, it is still necessary to date. I am not telling you to stop, I am just bringing this to the attention of the person packaging this. That's all.

---

### Post by sixstorm on 2007-02-28
Anybody wanna post any screenies?  

This packages is putting in the second to last piece in my girlfriend's complete conversion to Ubuntu.  Thanks in advance!!!

---

### Post by aysiu on 2007-02-28
I haven't tried out this .deb file.

mhancoc7, can you explain a bit more what exactly the .deb file is? Is it actually Internet Explorer itself bundled with Wine? Or does the .deb, like the IEs4Linux script, just fetch IE off the Microsoft site.

I don't know if that makes a legal difference, but I'd imagine fetching off MS's website wouldn't count as redistributing *per se*.

---

### Post by ~LoKe on 2007-02-28
It's a 7xMB download, so IE must be included.

---

### Post by Ramses de Norre on 2007-02-28
By looking through the contents I get the impression that it's a wrapper around IE4Linux' install script.
It puts IE4Linux in /usr/local/apps/ie4linux/ and runs it from there with wine, it doesn't install it's own wine but has it as dependency.

---

### Post by skywalker___ on 2007-02-28
:guitar: It works great  thank you...I like the home page too my best friend is a pastor..[SIZE="2"][/SIZE] and I was telling him how linux had a bible programs and how I think microsoft is evil any way thanks it works fine... I did have a problem installing it under  kde I just booted to gnome installed it fine their......

:

---

### Post by Raphink on 2007-02-28
Hi Jereme,

I hesitated posting here as I think you might think that once again I'm criticizing your work, but I'll have to agree with nixternal: this deb file is simply illegal, not to talk about the technical aspect.

While the ie4 scripts found a way to let people install IE6 on Linux without breaking the license, packaging the whole program in a deb is not allowed by the EULA that I know of, and once again I'm really sorry to see that the name of Ubuntu is being associated with it, even though the Ubuntu developers are trying hard to prevent such things to happen.

The only thing that would be allowed possibly, would be to have a deb package that only contains the ie4 scripts, install them (in a proper, FHS-compliant, location...) and run them. In any case, the use should be prompted the EULA and given a way to explicitely accept it (the use of debconf is a very good way to do that).

As long as this package contains the IE6 program, it is illegal.
As long as this package doesn't prompt the user for explicit agreement with the EULA, it is illegal.
If you can't do that, keep this package for yourself. I make illegal packages, too (that even are technically proper), but I keep them for my own usage because I care about respecting the law.

And once again, I'm not saying all this just for the pleasure of criticizing your work. I've warned you in the past about including proprietary software. I've proposed you to teach you how to make technically proper packages and work together with the Ubuntu community, and I've asked you as nicely as I could to please keep these things for yourself and not associate the name of Ubuntu with it (and yes, I don't hold the trademark, but I know I'm talking in the name of people who have high standards when it comes to licensing and respecting the law).

I am totally aware that many people are very happy to have this package, but it doesn't make it right. If I make a hold up in a bank and give all the money to the needy, I'm still a thief because I gave money I didn't own and broke the law, even though many people will be happy. You don't change a world you don't like by breaking its laws.


God bless

---

### Post by sixstorm on 2007-02-28
None of the plugins are working for me.  Java, Flash, nothing.  I was really hoping that this would work with any IE plugin so that way I could take VMWare off of my Linux install.  Good try my friend, hope your hard work doesn't get taken off the boards!

---

### Post by Altmenorg on 2007-02-28
1/ This package is totally illegal.
2/ This is the worst packaging ever...
3/ This is the kind of things that gives Ubuntu a bad reputation...

If you have a bit of logic, please remove this immediatly.

Just an example of the horrible packaging this is, launch lintian test on your deb package....
Several HUNDREDS of Warnings and Errors....

This is a pure shame...

---

### Post by skywalker___ on 2007-02-28
:guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar: 

come on guys light'n UP you sound like vista useers on paltalk 
I also installed ubuntu with a hate for windows and I love it this is the best help  I ever got with all the programs

---

### Post by ofek on 2007-02-28
> **Raphink said:**
> Hi Jereme,

I hesitated posting here as I think you might think that once again I'm criticizing your work, but I'll have to agree with nixternal: this deb file is simply illegal, not to talk about the technical aspect.

While the ie4 scripts found a way to let people install IE6 on Linux without breaking the license, packaging the whole program in a deb is not allowed by the EULA that I know of, and once again I'm really sorry to see that the name of Ubuntu is being associated with it, even though the Ubuntu developers are trying hard to prevent such things to happen.

The only thing that would be allowed possibly, would be to have a deb package that only contains the ie4 scripts, install them (in a proper, FHS-compliant, location...) and run them. In any case, the use should be prompted the EULA and given a way to explicitely accept it (the use of debconf is a very good way to do that).

As long as this package contains the IE6 program, it is illegal.
As long as this package doesn't prompt the user for explicit agreement with the EULA, it is illegal.
If you can't do that, keep this package for yourself. I make illegal packages, too (that even are technically proper), but I keep them for my own usage because I care about respecting the law.

And once again, I'm not saying all this just for the pleasure of criticizing your work. I've warned you in the past about including proprietary software. I've proposed you to teach you how to make technically proper packages and work together with the Ubuntu community, and I've asked you as nicely as I could to please keep these things for yourself and not associate the name of Ubuntu with it (and yes, I don't hold the trademark, but I know I'm talking in the name of people who have high standards when it comes to licensing and respecting the law).

I am totally aware that many people are very happy to have this package, but it doesn't make it right. If I make a hold up in a bank and give all the money to the needy, I'm still a thief because I gave money I didn't own and broke the law, even though many people will be happy. You don't change a world you don't like by breaking its laws.


God bless


Just wondering if this could be legal:
1. The .deb (or a script that will call the .deb file afterwards) would prompt and show u the EULA with the famous accecpt and decline options.
2. IE6 would be fetched from microsoft's website and not be bundled in the package its-self.

Although this way it would be really close to what ie4linux is. It will still be ezier for new users to immigrate to linux.

Note: the way all I mentioned would be achieved shouldn't matter for the sake of the question cuz it shouldn't be a problem. ( I'm a programmer although not very familiar with .deb packages )
I'm only asking to clarify so the one who packaged this could fix this so UBUNTU won't get to the news with illegal notices.

Sorry for my bad english and I hope someone who has better understanding on this subject could answer this.

---

### Post by nixternal on 2007-02-28
> **ofek said:**
> Although this way it would be really close to what ie4linux is. It will still be ezier for new users to immigrate to linux.

I don't think this is really a valid reason nor the type of thing we really want in order to "lure" new user in with. Any user, no matter the OS can easily switch to Firefox. If my very own grandmother and mother can do it, anybody can do it, even people who just turned a computer on for the first time.

---

### Post by ofek on 2007-02-28
> **nixternal said:**
> I don't think this is really a valid reason nor the type of thing we really want in order to "lure" new user in with. Any user, no matter the OS can easily switch to Firefox. If my very own grandmother and mother can do it, anybody can do it, even people who just turned a computer on for the first time.

Your probably right but: there are sites which for me work properly only with IE6+ capable browser (banking for once).

EDIT: after reading ur post again I see that ur problem with what I wrote is the reason for it and not that are no real and good reasons for having this kind of a .deb package.
The question we face is if this is legaly possible or not. Reasons for this can be subjective.

---

### Post by masteryurez on 2007-02-28
Internet Explorer works really good for me.. but it get an error first..
I installed it with the code
```
sudo dpkg -i internet-explorer-6-ubuntu_1.1_all.deb
```
and the installation gets an error.. Internet Explorer needs 3 more packets to be installed. I don't remember the packages name right now but if you install Internet Explorer in the terminal you will see the name of the 3 packages that is required. 

The 3 packages exists in Synaptec.

Good Luck!

---

### Post by mhancoc7 on 2007-02-28
> **nixternal said:**
> You do realize that you are in fact breaking the law?  First of all did the evil empire give you permission to do this? If so is that agreement in the package? Is there a EULA?  No matter how useful this application is to the masses, I don't feel for one that it is legal and two goes against everything the Ubuntu and Linux communities try to follow. Oh well, who am I to say though. Run lintian -i *.dsc before you pbuild it next time and take care of some of the packaging issues at least.

Well, the package does prompt the user to "Accept" the IE6 EULA. 

> **aysiu said:**
> I haven't tried out this .deb file.

mhancoc7, can you explain a bit more what exactly the .deb file is? Is it actually Internet Explorer itself bundled with Wine? Or does the .deb, like the IEs4Linux script, just fetch IE off the Microsoft site.

I don't know if that makes a legal difference, but I'd imagine fetching off MS's website wouldn't count as redistributing *per se*.

My initial plan was to have the deb package fetch ie6 from the web and install it. I ran into some problems with the EULA not displaying in wine. That section of the IE6 prompt was blank. So I decided to package it pre-installed and built a simple prompt using Gambas to display the EULA with the Accept/Decline buttons. I personally don't see what the big deal is since it is available via download and I am still requiring the acceptance fo the EULA. With that said, I understand that it might not be legal so I will remove it for now and see if I can package it within the law.


> **Raphink said:**
> Hi Jereme,

I hesitated posting here as I think you might think that once again I'm criticizing your work, but I'll have to agree with nixternal: this deb file is simply illegal, not to talk about the technical aspect.

While the ie4 scripts found a way to let people install IE6 on Linux without breaking the license, packaging the whole program in a deb is not allowed by the EULA that I know of, and once again I'm really sorry to see that the name of Ubuntu is being associated with it, even though the Ubuntu developers are trying hard to prevent such things to happen.

The only thing that would be allowed possibly, would be to have a deb package that only contains the ie4 scripts, install them (in a proper, FHS-compliant, location...) and run them. In any case, the use should be prompted the EULA and given a way to explicitely accept it (the use of debconf is a very good way to do that).

As long as this package contains the IE6 program, it is illegal.
As long as this package doesn't prompt the user for explicit agreement with the EULA, it is illegal.
If you can't do that, keep this package for yourself. I make illegal packages, too (that even are technically proper), but I keep them for my own usage because I care about respecting the law.

And once again, I'm not saying all this just for the pleasure of criticizing your work. I've warned you in the past about including proprietary software. I've proposed you to teach you how to make technically proper packages and work together with the Ubuntu community, and I've asked you as nicely as I could to please keep these things for yourself and not associate the name of Ubuntu with it (and yes, I don't hold the trademark, but I know I'm talking in the name of people who have high standards when it comes to licensing and respecting the law).

I am totally aware that many people are very happy to have this package, but it doesn't make it right. If I make a hold up in a bank and give all the money to the needy, I'm still a thief because I gave money I didn't own and broke the law, even though many people will be happy. You don't change a world you don't like by breaking its laws.


God bless

I honestly did not think that there was any problem since it is available via download. I will remove the package and work to get it within the law.

I must tell you however that I do not appreciate how you allows bring up how you have tried to help and teach me. I am not opposed to learning and I concede that I am no programmer. I just do not agree with you on many points. I think it is safe to say that you are working for the "long term" and I am working for the "short term". I think there is the need for both of us.

God Bless, Jereme

---

### Post by HasratUSA on 2007-02-28
> **nixternal said:**
> I don't think this is really a valid reason nor the type of thing we really want in order to "lure" new user in with. Any user, no matter the OS can easily switch to Firefox. If my very own grandmother and mother can do it, anybody can do it, even people who just turned a computer on for the first time.

Switching to Firefox is as easy as downloading the exe/executable file from mozilla's site and simply DOUBLE-CLICKING it. LoL those who still don't know how to double-click a file can stay with IE and mozilla users shouldn't waste time trying to encourage them. It's just fruitless and a mere waste of energy.

---

### Post by HasratUSA on 2007-02-28
> **ofek said:**
> Your probably right but: there are sites which for me work properly only with IE6+ capable browser (banking for once).

EDIT: after reading ur post again I see that ur problem with what I wrote is the reason for it and not that are no real and good reasons for having this kind of a .deb package.
The question we face is if this is legaly possible or not. Reasons for this can be subjective.

okay this is making me laugh. Which site are you talking about? Could you please be kind enough to post the URL so that I or anyone interested could pay a visit to the site in question and see what's going on?

If the site in question isn't really working in mozilla firefox, you should send a proper notification to the authorities concerned. After all, you're supposed to be their 'valued' customer.

Not too long ago I came across a news in, um, cnn (i guess but can't remember clearly), about one of the websites of Walmart  that prevented non-users of IE from accessing the site. it was about selling videos online, where you can go and pay a little money to download videos off their server. But as you already understand, the problem was that if you don't use IE, you wouldn't be able to use any of the features.

Several mozilla firefox and users of other browsers contacted Walmart by phone and email and most of them got a similar response, which is: Only IE is compatible with our site, and your concern/message would be sent to appropriate authorities concerned. thank you.

After that, as far as i know and as has been reported, even many IE fans stopped visiting the site and even boycotted any and every service provided by walmart, not to mention the usual mozilla firefox users. So many of them even stopped shopping in Walmart. And i don't know about the current status of the case.

As soon as the site came into the market, it announced grandly that it won't work with firefox and safari. Here is a brief overview: [http://www.centernetworks.com/walmart-in-bed-with-microsoft-no-to-firefox](http://www.centernetworks.com/walmart-in-bed-with-microsoft-no-to-firefox)

My recommendation is that you should try your best to talk to your bank authorities and make and force them to fix the problems. It's true that M$ has been playing some kinds of monopoly with their OS and browsers and many other stuffs over the past 5-6 years and let me tell you that they have been sued and defeated many times.

Sun Java was one of them who stood forward and filed a lawsuit against M$ and ultimately won the battle and got 20 million dollars from M$ as damage refund. You can read more about Sun's battle against M$ here: [http://www.internetnews.com/ent-news/article.php/988071](http://www.internetnews.com/ent-news/article.php/988071)

---

### Post by mhancoc7 on 2007-03-03
Ok, I have rewritten the app and it is now ready for users to take a look at. The program is now legal. Check the notes on the OP for more info.

You can get the .deb package here.
[http://www.ubuntulabs.devubuntu.com/deb](http://www.ubuntulabs.devubuntu.com/deb)

Thanks, Jereme

---

### Post by HasratUSA on 2007-03-03
> **Altmenorg said:**
> 1/ This package is totally illegal.
2/ This is the worst packaging ever...
3/ This is the kind of things that gives Ubuntu a bad reputation...

If you have a bit of logic, please remove this immediatly.

Just an example of the horrible packaging this is, launch lintian test on your deb package....
Several HUNDREDS of Warnings and Errors....

This is a pure shame...

This is a joke too :P

---

### Post by Raphink on 2007-03-05
> **mhancoc7 said:**
> Ok, I have rewritten the app and it is now ready for users to take a look at. The program is now legal. Check the notes on the OP for more info.

You can get the .deb package here.
[http://www.ubuntulabs.devubuntu.com/deb](http://www.ubuntulabs.devubuntu.com/deb)

Thanks, Jereme

Lintian is still very verbose:


------------------------ 8< ------------------------
E: internet-explorer-6-ubuntu: dir-in-usr-local usr/local/apps/
E: internet-explorer-6-ubuntu: dir-in-usr-local usr/local/apps/ies4linux/
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6.png
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6.png
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux.png
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux.png
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/install
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/install
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/configure
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/configure
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6_eula
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6_eula
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux.desktop
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux.desktop
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux-1.2.tar.gz
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux-1.2.tar.gz
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/dg_question
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/dg_question
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6
E: internet-explorer-6-ubuntu: no-copyright-file
W: internet-explorer-6-ubuntu: extended-description-line-too-long
E: internet-explorer-6-ubuntu: unknown-control-file copyright
E: internet-explorer-6-ubuntu: unknown-control-file changelog
------------------------ 8< ------------------------


For the file-in-usr-local and file-in-unusual-dir errors, please refer to the FHS and the Debian policy.

The package should contain a copy of the EULA in debian/copyright.

Description lines should not exceed 80 characters in order to fit in standard 80 columns terminals.

Do you have a source package for this anywhere? Does it build in an autobuilder (such as pbuilder)? I encourage you to use REVU and submit your package. Such a package, if done properly and compliant to the Debian policy and the law, could make it to the multiverse section.


God bless

Raphaël

---

### Post by mhancoc7 on 2007-03-05
> **Raphink said:**
> Lintian is still very verbose:


------------------------ 8< ------------------------
E: internet-explorer-6-ubuntu: dir-in-usr-local usr/local/apps/
E: internet-explorer-6-ubuntu: dir-in-usr-local usr/local/apps/ies4linux/
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6.png
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6.png
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux.png
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux.png
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/install
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/install
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/configure
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/configure
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6_eula
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6_eula
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux.desktop
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux.desktop
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ies4linux-1.2.tar.gz
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ies4linux-1.2.tar.gz
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/dg_question
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/dg_question
E: internet-explorer-6-ubuntu: file-in-usr-local usr/local/apps/ies4linux/ie6
W: internet-explorer-6-ubuntu: file-in-unusual-dir usr/local/apps/ies4linux/ie6
E: internet-explorer-6-ubuntu: no-copyright-file
W: internet-explorer-6-ubuntu: extended-description-line-too-long
E: internet-explorer-6-ubuntu: unknown-control-file copyright
E: internet-explorer-6-ubuntu: unknown-control-file changelog
------------------------ 8< ------------------------


For the file-in-usr-local and file-in-unusual-dir errors, please refer to the FHS and the Debian policy.

The package should contain a copy of the EULA in debian/copyright.

Description lines should not exceed 80 characters in order to fit in standard 80 columns terminals.

Do you have a source package for this anywhere? Does it build in an autobuilder (such as pbuilder)? I encourage you to use REVU and submit your package. Such a package, if done properly and compliant to the Debian policy and the law, could make it to the multiverse section.


God bless

Raphaël

Thanks  Raphaël,
That would be awesome. I have just installed the debian-policy and I will be taking a look at it soon. Who knows, maybe me and you will work together on something after all. :) Really, thank you!

The source is located within the .deb package. I am sure this is not the correct way to do it. I will try to see if I can start to properly package my .deb packages.

God Bless, Jereme

---

### Post by DarkN00b on 2007-03-05
HA! This is funny. I went to Windows Update and got two security updates -- thanks Microsoft! :D

Posting this from IE in Ubuntu now...

---

### Post by Raphink on 2007-03-06
> **mhancoc7 said:**
> Thanks  Raphaël,
That would be awesome. I have just installed the debian-policy and I will be taking a look at it soon. Who knows, maybe me and you will work together on something after all. :) Really, thank you!

The source is located within the .deb package. I am sure this is not the correct way to do it. I will try to see if I can start to properly package my .deb packages.

God Bless, Jereme


The packaging guide available on [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html) should help you work on the source package.
You can also look at the reviewing tips on [https://wiki.ubuntu.com/MOTU/Packages/Reviewing](https://wiki.ubuntu.com/MOTU/Packages/Reviewing) .


God bless

Raphaël

---

### Post by skywalker___ on 2007-03-06
HAHAHAHHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAH

DarkNoob

:guitar: :guitar: :guitar:

---

### Post by mhancoc7 on 2007-03-06
> **skywalker___ said:**
> HAHAHAHHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAH

DarkNoob

:guitar: :guitar: :guitar:

Just think, a few hundred more quality posts like that one and you might just be a "Ubuntu Roast Master"! :lolflag:

Jereme

---

### Post by amphet on 2007-03-06
Nice, I want to help with this package, gonna try it when I get home.

cheers

---

### Post by Icarosaurus on 2007-03-06
Is there some way for making ies4linx agree with winetools?
I cannot install iexplore with winetools but ies4linux works fine.
But It doesn't fit with the winetools fake c drive...

---

### Post by mhancoc7 on 2007-03-06
> **Icarosaurus said:**
> Is there some way for making ies4linx agree with winetools?
I cannot install iexplore with winetools but ies4linux works fine.
But It doesn't fit with the winetools fake c drive...

The way ies4linux installs is in a seperate wine directory. I like this because it does not mess with the users wine directory. You could probably tweak the ies4linux script to have it use your existing wine directory.

Jereme

---

### Post by Raphink on 2007-03-16
Hi Jereme,

Any news from a source package for the IE6 and e-sword deb yet?


God bless

Raphael

---

### Post by mhancoc7 on 2007-03-16
> **Raphink said:**
> Hi Jereme,

Any news from a source package for the IE6 and e-sword deb yet?


God bless

Raphael

I have not had time to take a look at exactly how to put together a source package. The source is included in the .deb now. The source includes all of the scripts and the GUI created in Gambas. I packaged the GUI source using Gambas and just included it in the ies4linux directory in the deb. I realize this is probably not the right way to do it.

Thanks, Jereme

---

### Post by Raphink on 2007-03-16
> **mhancoc7 said:**
> I have not had time to take a look at exactly how to put together a source package. The source is included in the .deb now. The source includes all of the scripts and the GUI created in Gambas. I packaged the GUI source using Gambas and just included it in the ies4linux directory in the deb. I realize this is probably not the right way to do it.

Thanks, Jereme


I totally understand your lack of time :)

If you're not interested in releasing a source package, could you provide a tar.gz with all your files and scripts (including the version number in the tar.gz), COPYING/LICENSE files and where to install each thing (a Makefile would be much better, but I'll do it if you don't want to) so I can make such a thing and work on a widely distributable version of these packages?

Thank you for your work


Raphael

---

### Post by mhancoc7 on 2007-03-16
> **Raphink said:**
> I totally understand your lack of time :)

If you're not interested in releasing a source package, could you provide a tar.gz with all your files and scripts (including the version number in the tar.gz), COPYING/LICENSE files and where to install each thing (a Makefile would be much better, but I'll do it if you don't want to) so I can make such a thing and work on a widely distributable version of these packages?

Thank you for your work


Raphael

Will these work? 

Yeah, my wife and I are expecting our second child any day now. I believe I saw something about you having a special day coming up on the Ichthux forums. If so, Congratulations!

God Bless, Jereme

---

### Post by Raphink on 2007-03-17
> **mhancoc7 said:**
> Will these work? 

Ok I'll have a look.


> Yeah, my wife and I are expecting our second child any day now. 

Congratulations :) 


> I believe I saw something about you having a special day coming up on the Ichthux forums. If so, Congratulations!

Yes, I'm getting married in a month :)

---

### Post by mhancoc7 on 2007-03-17
> **Raphink said:**
> Ok I'll have a look.




Congratulations :) 




Yes, I'm getting married in a month :)

Thanks, and Congratulations to you again. I hope you have a wonderful wedding!

God Bless, Jereme

---

### Post by ]Nbx*cmD[ on 2007-03-17
Hmm, for me the problem is not about legal issues...

I've been fighting hard in all the areas i could to make website developers stick to the web standards. IE doesn't give a thing about the standards and gives lots of trouble to us, the free software users.

The way to solve this problem is not to try to make propietary and non-standarized software work in our computers, but to fight for the complete conversion to free software. It's a long fight, but the only valid one.

I do not criticize your work though, i just noticed that everybody was talking about legal issues without mentioning this other problem.

---

### Post by Raphink on 2007-03-17
> **']Nbx*cmD[ said:**
> Hmm, for me the problem is not about legal issues...

I've been fighting hard in all the areas i could to make website developers stick to the web standards. IE doesn't give a thing about the standards and gives lots of trouble to us, the free software users.

The way to solve this problem is not to try to make propietary and non-standarized software work in our computers, but to fight for the complete conversion to free software. It's a long fight, but the only valid one.

I do not criticize your work though, i just noticed that everybody was talking about legal issues without mentioning this other problem.

I totally agree with you. I for one do not rejoice in packaging proprietary software at all. But I like even less the idea of messing up users' computers, so if such a thing as IE and e-sword package are to exist, I would rather them be official packages in Ubuntu multiverse than unofficial debs distributed on third party websites.


Raphael

---

### Post by Raphink on 2007-03-17
> **mhancoc7 said:**
> Thanks, and Congratulations to you again. I hope you have a wonderful wedding!

God Bless, Jereme


Jereme,

If I redo the packages according to the Debian policy, do you want to be marked as the maintainer, or shall I be the maintainer?

This is not a copyright issue (I'll be keeping your name as the original packager anyway in the debian/copyright file), but a responsability of keeping it up-to-date and compliant to the Debian policy.

I would be happy if you would be willing to take this responsability, but I will understand if you want me to have it.


God bless

Raphael

---

### Post by mhancoc7 on 2007-03-17
> **Raphink said:**
> Jereme,

If I redo the packages according to the Debian policy, do you want to be marked as the maintainer, or shall I be the maintainer?

This is not a copyright issue (I'll be keeping your name as the original packager anyway in the debian/copyright file), but a responsability of keeping it up-to-date and compliant to the Debian policy.

I would be happy if you would be willing to take this responsability, but I will understand if you want me to have it.


God bless



Raphael

I would be happy to be the maintainer. These will make great examples for me to follow when packaging. I would like to know exactly how the way I have them packaged could "break" someone's system. So far there have been no issue like that with the packages that I have built. I know that they are not up to Ubuntu standards, but they work and seem to be perfectly acceptable to the thousands of users who have downloaded them.


God Bless, Jereme

---

### Post by elektronaut on 2007-05-27
BE CAREFUL ABOUT INSTALLING / UNINSTALLING THIS!!!

I downloaded the package from [http://www.ubuntulabs.devubuntu.com/deb/](http://www.ubuntulabs.devubuntu.com/deb/). As an error was reported at the end of the installation process, I uninstalled it again. Afterwards the bin directory in my home directory was gone! There were a lot of scripts that I had written...
I already informed the OP about this, so he can add a warning.

---

### Post by mhancoc7 on 2007-05-28
> **elektronaut said:**
> BE CAREFUL ABOUT INSTALLING / UNINSTALLING THIS!!!

I downloaded the package from [http://www.ubuntulabs.devubuntu.com/deb/](http://www.ubuntulabs.devubuntu.com/deb/). As an error was reported at the end of the installation process, I uninstalled it again. Afterwards the bin directory in my home directory was gone! There were a lot of scripts that I had written...
I already informed the OP about this, so he can add a warning.

Thanks for alerting me to this issue.

I have released a new version that fixes the issue. I have also updated the convert_me script. I will be releasing the new iso soon.

Jereme

---

