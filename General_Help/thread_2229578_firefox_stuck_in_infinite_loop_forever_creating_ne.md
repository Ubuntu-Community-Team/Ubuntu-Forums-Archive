---
title: "firefox stuck in infinite loop forever creating new blank tabs"
date: 2014-06-13
forum: General Help
---

### Post by the big e on 2014-06-13
This is a recent fresh-install dual-boot ubuntu 14 and Windows Vista.

While using Windows, I found an intersting URL about something I wanted to install in Ubuntu. 

I saved a shortcut into a folder within my Windows "Documents" folder and later tried to read it in Firefox within Ubuntu.

This caused my Firefox to go into an infinite loop where it does nothing but create hundreds of new blank tabs.

Until it crashes, I guess.

If I quit Firefox, it re-starts and starts creating more blank tabs. (it created as many as 699 of them in one go-round)

I tried un-installing and re-installing Firefox, but that was not sufficient to stop this behavior.

What in the world is going on?

I finally un-installed Firefox and I am using a different browser now.

---

### Post by monkeybrain20122 on 2014-06-14
It is a malware site? 

Close Firefox, open the file manager at your home, press ctr+h or click 'show hidden files' from menu, find the hidden folder .mozilla (note the '.') and delete it.

---

### Post by the big e on 2014-06-14
I saw no malware, it looked like a real thing to me.

What I did notice, though, is that the address that showed up in the input line of Firefox when I tried to open the shortcut was the location of the shortcut on my hard drive, rather than the location on the web of the URL I was trying to reach.

So it seems that it was somehow parsing the shortcut as a direction to itself, rather than a direction to somewhere on the web, and directing itself to open itself in a new window over and over again.

I did delete the .mozilla folder as you suggested, and will never know whether or not that was the thing that was necessary.

(I have seen Firefox malware that re-starts Firefox on the same web page over and over, though. Un-installing and re-installing Firefox did the trick for me in that case.)

---

### Post by pretty_whistle on 2014-06-14
It's not malware.  I only have Ubuntu and I had this same problem about a week ago.  I wish I could recall how I fixed it :( but I dont.

I was able to make Firefox stop by restarting the computer.

Sorry I dont recall how I fixed it but it's fixable fwiw.

---

### Post by the big e on 2014-06-19
and it did another weird thing a little while ago.
when you quit it gives a dialog box about how many tabs you are closing.
I got multiple copies at once of that dialog box.

---

