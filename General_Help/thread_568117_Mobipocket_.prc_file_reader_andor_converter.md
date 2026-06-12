---
title: "Mobipocket .prc file reader and/or converter?"
date: 2007-10-05
forum: General Help
---

### Post by got2av8 on 2007-10-05
I'm wondering if anyone knows of an app that might allow me to read/open Mobipocket .prc ebook files in Ubuntu.  I saw the information on the .lit file converter in an earlier thread, but so far I haven't been able to find a definitive answer for .prc.  Anyone want to comment?  Please don't tell me I have to boot Vista to read my magazines...

---

### Post by got2av8 on 2007-10-05
Oh, and I should also say that I'm in the middle of getting WINE set up, so that's always a fallback option, but it really seems to be going against the spirit of the thing. ;)

---

### Post by LaneLester on 2008-05-19
I'm sorry to see no one has posted a solution for this. I have a ton of Mobipocket .prc files I'd love to be able to access in Linux. I tried FBReader, but it said it didn't recognize the compression in the .prc file.

Lane

---

### Post by Megalorian on 2008-05-27
I would be curious to know as well. Has anyone gotten it running under wine?

---

### Post by moon_song on 2008-06-24
Hey, 

Don't know if anyone is still interested in it but I just managed to get Mobipocket working under Ubuntu 8.04.

I downloaded the archived version from their website, the one for Windows98. I copied the installer in the .wine directory under Program Files and ran wine MobipocketReaderPC.exe (name of installer). It's of course not necessary to copy the installer in the Program Files directory, but I did it to keep all the things in one place. 

In any case the installation went peachy until I tried to actually start the program; I got an error message that the file msvcp60.dll was needed for the launching. I got that file from the net (plain google, god bless it) and copied it into the Mobipocked directory in Program Files under wine. 

After that I attempted to open Mobipocket reader again and it works like a charm :) 

You will have to register it again, with whatever ebook site you are using, at least i had to and then you can start reading :) 

enjoy 

PS: here is where you can get the .dll file and the installer I used (the XP version of Mobipocket did not work for me in Wine, dunno why)

[http://www.dll-files.com/dllindex/pop.php?msvcp60]("http://www.dll-files.com/dllindex/pop.php?msvcp60")

[http://www.mobipocket.com/en/DownloadSoft/DownloadManualInstall.asp#archivedVersion]("http://www.mobipocket.com/en/DownloadSoft/DownloadManualInstall.asp#archivedVersion") - scroll down at the end of the page :)

Hope this helps someone. In case it's old news :"> I apologize, I'm new at this whole linux thing (yes, yes, I know you've heard it 1000 times, but it's true :p )

Enjoy, 

Me :):guitar:

---

### Post by LaneLester on 2008-06-24
> **moon_song said:**
> Hey, 

Don't know if anyone is still interested in it but I just managed to get Mobipocket working under Ubuntu 8.04.

Thanks a big bunch for posting this! I am very interested, and I'm pleased to report that it worked perfectly on my Xubuntu Hardy machine. I ran wine on the install program without putting it in Program Files, and it worked fine. But I copied the .dll in before trying to run the program.

Now to see if it will work on my Eee PC running Xandros!

Lane

---

### Post by moon_song on 2008-06-24
Welcome :) and good luck :p

Je:popcorn:

---

### Post by Zebaztian on 2008-07-13
> **moon_song said:**
> Hey, 

Don't know if anyone is still interested in it but I just managed to get Mobipocket working under Ubuntu 8.04.

I downloaded the archived version from their website, the one for Windows98. I copied the installer in the .wine directory under Program Files and ran wine MobipocketReaderPC.exe (name of installer). It's of course not necessary to copy the installer in the Program Files directory, but I did it to keep all the things in one place. 

In any case the installation went peachy until I tried to actually start the program; I got an error message that the file msvcp60.dll was needed for the launching. I got that file from the net (plain google, god bless it) and copied it into the Mobipocked directory in Program Files under wine. 

After that I attempted to open Mobipocket reader again and it works like a charm :) 

You will have to register it again, with whatever ebook site you are using, at least i had to and then you can start reading :) 

enjoy 

PS: here is where you can get the .dll file and the installer I used (the XP version of Mobipocket did not work for me in Wine, dunno why)

[http://www.dll-files.com/dllindex/pop.php?msvcp60]("http://www.dll-files.com/dllindex/pop.php?msvcp60")

[http://www.mobipocket.com/en/DownloadSoft/DownloadManualInstall.asp#archivedVersion]("http://www.mobipocket.com/en/DownloadSoft/DownloadManualInstall.asp#archivedVersion") - scroll down at the end of the page :)

Hope this helps someone. In case it's old news :"> I apologize, I'm new at this whole linux thing (yes, yes, I know you've heard it 1000 times, but it's true :p )

Enjoy, 

Me :):guitar:

Thx, this was perfect, it means that I can borrow books from the library :popcorn:

But I think that FBReader [http://www.fbreader.org](http://www.fbreader.org) is something that will come more and more. FBReaderJ 0.2 for Google Android was recently released. It means that all publishers will somehow support their books for FBReader, because Google is a very important player in this field. :guitar:

---

