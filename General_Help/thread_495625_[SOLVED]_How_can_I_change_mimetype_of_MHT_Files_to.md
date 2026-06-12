---
title: "[SOLVED] How can I change mimetype of MHT Files to NOT be Plain Text but Web Page Arc"
date: 2007-07-08
forum: General Help
---

### Post by OzzyFrank on 2007-07-08
I save many web pages with pictures as MHT files (the only good thing about Internet Explorer, and the reason I use Opera in Windows and Ubuntu). Problem is, Ubuntu looks at them as just another type of plain text, which of course is the total opposite. If I try to change MHT files to open in Opera, next thing all text files are being opened in that too (which of course means I can't edit them). How can I easily change the mimetype of MHT files to be something different, preferably a new type I can assign Opera to?

---

### Post by oomingmak on 2007-07-08
I'd really like to know this too (although for me that's only half the equation). The other part is getting Firefox to actually display it rather than pop up a dialog to save it or hand it off to another application.

---

### Post by OzzyFrank on 2007-08-05
Still no takers on this huh? Well, hope someone in the development dept noticed, as it is a bit sad that MHTML files are treated as plain text in Ubuntu. And I don't want my text files opening in Opera, hehe!

---

### Post by oomingmak on 2007-09-04
> **OzzyFrank said:**
> I save many web pages with pictures as MHT files (the only good thing about Internet Explorer, and the reason I use Opera in Windows and Ubuntu). Problem is, Ubuntu looks at them as just another type of plain text, which of course is the total opposite. If I try to change MHT files to open in Opera, next thing all text files are being opened in that too (which of course means I can't edit them). How can I easily change the mimetype of MHT files to be something different, preferably a new type I can assign Opera to?
I've managed to figure out a way to get this working.

See my post here: 

[[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG][SIZE=4][COLOR=DarkOrange]**[COLOR=White].[/COLOR]Link**[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?p=3311005#post3311005")

(If you don't want to open your .mht files in Firefox, then ignore the stuff about the MAF extension and just follow the instructions in Step 5.)

---

### Post by OzzyFrank on 2007-09-04
Hi, and thanks for that! I've yet to try Assogiate, but looks simple to use so will make my mimetype tonight. Just thought I'd add a link to the .deb version for others who might want it:

[http://mirrors.kernel.org/ubuntu/pool/universe/a/assogiate/assogiate_0.2.1-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/a/assogiate/assogiate_0.2.1-0ubuntu1_i386.deb)

And yes, because I use Opera that supports .mht archives natively, I won't have to go through all that fuss to try to get it to work with Firefox (which saves .mht files in some weird format anyway, by the sounds of things).

Anyway, I've tried manually creating my own mimetype, but it wouldn't stick, so hopefully Assogiate does the trick. Cheers

---

### Post by oomingmak on 2007-09-05
> **OzzyFrank said:**
> Hi, and thanks for that!

No problem. :cool:

> **OzzyFrank said:**
>  Just thought I'd add a link to the .deb version for others who might want it:

[http://mirrors.kernel.org/ubuntu/pool/universe/a/assogiate/assogiate_0.2.1-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/a/assogiate/assogiate_0.2.1-0ubuntu1_i386.deb)

Great! I'm sure that there are loads of people who would rather not mess around compiling it from source (like I had to do) so having a .deb available is good news.

> **OzzyFrank said:**
>  Anyway, I've tried manually creating my own mimetype, but it wouldn't stick, so hopefully Assogiate does the trick.

Well Assogiate won't tell you what settings to use (so you still have to figure that part out for yourself) but it's still a hell of a lot easier than hand-editing [COLOR=Sienna][COLOR=Black]freedesktop.org.xml. 

The [[COLOR=DarkOrange]**settings **[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3311005#post3311005")that I stated (in step 5 of my .url thread) work perfectly on my system. I've even managed to get it so that I have different icons displayed depending on whether the .mht file was created by IE or by MAF in Firefox (and this works despite the fact that they both have the exact same '.mht' file extension). The different icons makes it easy to figure out the compatibility of the .mht file just by looking at it.

I hope it works out for you too this time.
[/COLOR][/COLOR]

---

### Post by kdau on 2007-09-11
Unfortunately, that .deb link is for Gutsy, the upcoming Ubuntu version which will be released in October. Users of Feisty (the current version, released in April) should either install from source or wait until next month. Once Gutsy is released, assoGiate can be installed from Synaptic (or possibly Add/Remove), so the .deb link won't be necessary.

---

### Post by OzzyFrank on 2007-09-12
Hi, and thanks to [COLOR="#9932cc"]**kdau**[/COLOR] (from Assogiate) for replying to my query (regarding dependencies failing with the deb installer) which I sent from the official site. To fill the rest of you in, the deb will result in the error that the dependency "**libc6**" is unfulfilled, even though it is installed. Installing the rest of the Debian packages needed (mentioned on the dowload page) still produces the same result, which means that you ain't gonna get this happening with Feisty or lower. To quote kdau:

[COLOR="DarkOrchid"]You should use Synaptic to remove the assogiate package you installed.[/COLOR]
(That isn't needed, since it wouldn't install anyway)
[COLOR="#9932cc"]When you upgrade to Gutsy next month, you can install the program normally.

If you want to install from source now, download the source .tar.gz file
[1], then follow the instructions at [2]. Be sure to keep the resulting
folder around until you install Gutsy. Then (next month), use "sudo make
uninstall" inside that folder (as described in [2]) to get rid of your
manual copy before installing the official one.

[1] <http://www.kdau.com/files/assogiate-0.2.1.tar.bz2>
[2] <http://monkeyblog.org/ubuntu/installing/#source>[/COLOR]

I had already figured compiling the tarball I also downloaded would be the best bet, but couldn't figure out why it wouldn't install. So I went back to the site and saw the tarball is around 360Kb but I had ended up with one only 175Kb, hehe... so I thought I'd put the links here to save people going to the site looking for it. Also I thought I may as well leave the link to the installing from source guide for those who need it (it's a very good page).

Anyway, once I had a tarball that wasn't corrupt it installed easily, and following that great guide from [COLOR="Blue"]**oomingmak**[/COLOR] I quickly and easily got the .MHT extension I've been hanging for! That has some pretty detailed settings etc that I wouldn't have figured out myself, so **many** thanks once again. I didn't need to do all that extra stuff for Firefox, since I use Opera that handles MHT archives, but that is awesome nonetheless! I'm tempted to do it just for the hell of it!

So thanks to all for your great help, and I'm gonna mark this baby as [SOLVED]! Cheers.

---

### Post by oomingmak on 2007-09-16
> **OzzyFrank said:**
> following that great guide from [COLOR=Blue]**oomingmak**[/COLOR], I quickly and easily got the .MHT extension I've been hanging for! It has some pretty detailed settings etc that I wouldn't have figured out myself, so **many** thanks once again. 
No problem.

:-D

I'm glad to hear that it worked for you.

---

