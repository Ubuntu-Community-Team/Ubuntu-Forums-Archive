---
title: "How to: Use your 3rd Generation (3g) iPod in Ubuntu (&amp; and Windows)"
date: 2008-05-02
forum: General Help
---

### Post by smoothununtu on 2008-05-02
Like many people, I got a 3rd Generation iPod Nano for Christmas last year.  All in all, I have been very pleased with the operation and functionality of the iPod.  The hardware is fantastic, it is the iTunes software that I don't really care for.  

     Apple has seen fit to force users to use iTunes to upload music or movies the ipod.  To make matters worse, by default, you can't even see the iPod as a device unless you check the "Enable disk use" box in iTunes.  And once you upload the media to the iPod, iTunes renames the file on the iPod to some crazy name.    
 
     Say you copied a song called funky dance.mp3 to your ipod; iTunes then renames the file something like BZRT.mp3.  So if you ever just want to plug your ipod into the pc and just play a song, without iTunes, you would basically click on your music files until you found the renamed version of funky dance.mp3

Worst of all, was there was NO SUPPORT for 3rd Generation iPod's in LINUX ---- **Until NOW!!!**

I came across this little article yesterday, and WOW, it REALLY WORKS (and doesn't rename the file to like BZRT.mp3)!!!!!

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/]("http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/")



***** Even though the article says to run the files in this order:**

libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb
libgpod2_0.5.3+actually0.6.0-0.1_i386.deb 

I found that it did not work.  It was missing dependencies.
[B]
So install the files in this order:

libgpod2_0.5.3+actually0.6.0-0.1_i386.deb 
libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb[/B]


One other important note: Depending on the name of your ipod, you may have to go a Windows machine and rename the ipod device name to some  name like **ipod**.  For example my ipod's name was like Bob's Ipod.  Anyway in Windows, Go to My Computer, right click on the device, and click rename.  Then name it **ipod**. 

I had trouble running:  /usr/bin/ipod-read-sysinfo-extended /dev/sdb1 /media/Bob's IPOD

But when I renamed the it to just the word ipod, this command worked perfectly

 **/usr/bin/ipod-read-sysinfo-extended /dev/sdb1 /media/IPOD**

Just in case the URL above is no longer valid, here is a copy of the article.

-----------------------------------------------------------------

On the Road : Victoria J.K. Lamburn’s Blog
Virgin Mobile Praise + Ubuntu and iPod Nano 3g
Posted in Uncategorized by lilserenity on December 22nd, 2007

I have nothing but praise for Virgin Mobile. Certainly the best carrier I have been on as they are backed by T-Mobile’s rather good network. (Can’t remember when I was last without signal and I tend to go to remote places.) Anyway remember my post about Virgin Mobile’s recent offer if you take out an 18 month contract at £25 or more a month (new or existing customers) you could choose from an iPod nano, PSP Slim or £100 credit? Well they’ve turned up the goods before Christmas.

Even better is that they rang me on Wednesday to say that it was going to be dispatched and confirm it was the iPod I had chosen. Excellent service.

So yesterday I went over to Newhaven to get it. On the way I understood why Yahoo’s Weather had been telling me on Worthing.gov.uk that the weather was FOG. It seems the whole of Shoreham, much of Brighton & Hove and East Sussex beyond that was covered in some of the worst freezing fog we’ve had in a long time. Couldn’t see bloody 3ft in front of me in the car. Anyway got back safely and have unwrapped it. The packaging is a lot smaller than when I used to work selling Apple gear and iPods in ‘05. I remember iPods coming in big cube shaped boxes (mostly because Apple actually included the accessories you need.. another story) and I was there for the iPod nano’s first generation’s launch and those boxes were in themselves pretty tiny compared to the iPod 4g’s and Minis. Now it’s stupidly tiny!

Anyway I’m no fan on iTunes on Windows. The last time I used it was on Mac OS X 10.4.8 I would guess and iTunes 7 actually ran perfectly fine on a G4 1.4GHz but on Windows, I have yet to see a PC that bats it around like a little play thing. It’s a dog. Plus I don’t wish to be locked into DRM either. So iTunes is a no go.

Especially when my ThinkPad runs Ubuntu and to top it all; my Dell GX240 runs Windows 2000 now (another thing to write up) and the iPod Classic and Nano 3g require Windows XP SP2 or Vista.  Long and short of it is that to remain legal and to keep my Nikon Coolscan LS-30 working I have to stick with Windows 2000.

Easy ways to get iPod Nano 3g/Third Generation and Classics working without iTunes:

Windows:

    * MediaMonkey 3 (Currently on RC-5) — very good. Works on Windows 98/ME/2000/XP and Vista. Much more lightweight but very full features. Supports iPod Nano 3g and Classic out of the box. Freeware with paid for version offering all features. Download Version 3 Release Candidate. (Version 2 does not support the new iPods)

Ubuntu / Debian Linux in general

THIS IS ONLY NEEDED FOR iPOD NANO 3rd GENERATION or iPOD CLASSIC MODELS (FALL 2007 MODELS)

   1. Download from here: [ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/) the following packages:

      libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb
      libgpod2_0.5.3+actually0.6.0-0.1_i386.deb
   2. Install them in that order (double click their icons)
   3. Plug in the new iPod with the supplied USB docking cable
   4. Open up a shell/terminal
   5. Enter the command df (press enter) and look for the line that has /media/IPOD/ at the end at the very start of the line should be something that reads /dev/sdb1 or similar. Make a note of this.
   6. Enter as root user with: sudo bash and enter your password. (Ubuntu)
   7. Run the following:

      /usr/bin/ipod-read-sysinfo-extended [/dev/xxxx] /media/IPOD

      Where [dev/xxxx] is the /dev path you made note of in step     5. E.g. my iPod registered on /dev/sdb1 so I would enter:

      /usr/bin/ipod-read-sysinfo-extended /dev/sdb1 /media/IPOD
   8. Eject the iPod (right click on the iPod icon on the desktop and select Eject), close the terminal.
   9. Plug in the iPod again, Rhythmbox should automatically run and now you should be able to manage your new iPod through Rhythmbox again.

Why and Final Words
You have to do this as Apple added a layer of encryption to lock you into using iTunes which I personally think is wrong. What is wrong Apple with me using a player that I like? Two faced-ness abounds from Apple on such matters considering their rhetoric on Microsoft and the Windows empire.

But the good thing is that both Windows and Linux users now have an alternative to iTunes and also for Linux a way of actually being able to use their new iPod.

Plus you don’t absolutely have to run Windows XP or Vista on the Windows side. I appreciate XP and Vista account for about ~85% of the Windows marketplace these days but Windows 2000 still takes a sizable 8% of that according to web statistics I collect, which is more than the Mac accounts for, so Windows 2000 isn’t too insignificant to ignore yet!

-----------------------------------------------------------------


[I]
By the way, I tried Media Monkey (the Free Windows product)and it worked as well(in Windows, not Ubuntu).[/I]

---

### Post by cmpunk on 2008-08-17
hey, followed the steps and i downloaded it, but i couldnt install it. Every time i would click install and after 30 seconds it would say installation failed. Is there a way to fix this?

---

