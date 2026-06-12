---
title: "library computers, keeping history. need ISO help"
date: 2015-01-17
forum: General Help
---

### Post by disturbed13 on 2015-01-17
and now that my title has you confused or wondering what i am saying. allow me to explain my issue.

the other day i was using a computer at my local library and noticed that when i started to fill a menu out, there was a history. okay no big deal, i started to type numbers.... and 9 digits came up.... big deal. they looked like social security numbers, an identity thefts wet dream on the screen (its a good thing none of them were mine). so i attempted (to no vail) to add a history clearing program (this is on a windows machine) and as i suspected upon restart the program was gone, a safe guard/ card is in place. a program that prevents anything from being installed.

so my thought is to use a live ISO of Ubuntu, but here is where i need help. i dont need games, and i need it to be as 'thin' (in terms of size) as possible. and i would like to have Tor installed as well, and maybe terminator.

**so my question:**

how can i take an ISO and remove all of the parts that i dont want, and add the programs that i do want then burn it to a DVD or have a flash drive with the live OS with the adjusted programs running?



any thoughts or advise on how i should proceed would be greatly appreciated.

FYI: i also told the librarians about the security issue, they brushed me off. i also sent an email to the IT department of the library and i will continue to try and get this resolved.

---

### Post by Holger_Gehrke on 2015-01-17
There are specialized mini distribution for just this kind of situation.Follow the link to distrowatch in 'Useful Links' in the forum's menu bar.
One possible problem: if they have secured the machines against installation of programs, how good do you think your chances are of booting another OS on these PCs ?

---

### Post by grahammechanical on 2015-01-17
What is stopping you from installing a Linux distribution on to the USB memory stick "with persistence" and then use the software Centre to remove any applications that you do not want?  There are 3 Tor related applications in the Ubuntu Software Centre.

---

### Post by disturbed13 on 2015-01-17
> **Holger_Gehrke said:**
> There are specialized mini distribution for just this kind of situation.Follow the link to distrowatch in 'Useful Links' in the forum's menu bar.
One possible problem: if they have secured the machines against installation of programs, how good do you think your chances are of booting another OS on these PCs ?

because if i boot an OS from a different media, the installation block wont exist. just as a virus wont exist if you dont initilize the executeable on the HDD.

> **grahammechanical said:**
> What is stopping you from installing a Linux distribution on to the USB memory stick "with persistence" and then use the software Centre to remove any applications that you do not want?  There are 3 Tor related applications in the Ubuntu Software Centre.

i really didnt think of that, i guess im old school

---

### Post by yancek on 2015-01-17
> One possible problem: if they have secured the machines against  installation of programs, how good do you think your chances are of  booting another OS on these PCs ?

I think what was meant as the library computers may not allow booting from a CD/DVD/flash drive.  You could ask.

---

### Post by Bucky Ball on 2015-01-17
Much better to go the other way. Use the [mini.iso ]("https://help.ubuntu.com/community/Installation/MinimalCD")then add only the things you want. It installs only the base Ubuntu kernel and you do the rest (including adding the desktop environment that suits). This is always how I install on any machine. No use for apps I'll never use. ;)

Trying to strip back a full install is problematic.

---

### Post by disturbed13 on 2015-01-17
thats really good advise!
thanks!

---

### Post by nerdtron on 2015-01-17
After reading the first post, you don't want history when browsing on a windows machine? Isn't the "incognito mode" in chrome or "private browsing" in firefox do this already? After closing firefox private browsing, all history and cookies will be erased. It will looked like you did not open firefox if you use this.

---

### Post by disturbed13 on 2015-01-18
> **nerdtron said:**
> After reading the first post, you don't want history when browsing on a windows machine? Isn't the "incognito mode" in chrome or "private browsing" in firefox do this already? After closing firefox private browsing, all history and cookies will be erased. It will looked like you did not open firefox if you use this.

it doesnt have chrome or firefox
and i cant install anything on them
so its a no go

---

### Post by nerdtron on 2015-01-18
Sure you can't install as the windows machines could be locked. But if you are allowed to plug a USB and run an application you can carry your own firefox/chrome. 
[http://www.portableapps.com](http://www.portableapps.com)

Just download the portable firefox, install to your flash drive and plug it on any computer. Run your own version and carry all your browsing data with you. No traces on the machine.

---

### Post by amanchesterman on 2015-01-18
I don't know where you live, but I am in NW England and I used to teach computing (the basics of browsing, email, wordprocessing etc.) in our local public libraries.

As you say, the machines would sometimes remember data that had been entered in form fields. The librarian told me that it was because users did not properly log out of their sessions when they finished: they would go to a website, enter their data to transact their business and then maybe log out of the site, but would then forget to terminate their user session on the machine. (They would just walk away.)

So besides the advice you've been given above, you may want to check whether something similar applies in your case. If in doubt, turn off the machine when you have finished it. (The library machines I used were set to close down and restart automatically once every 24 hours, to ensure that all user-entered data were cleared.) Ask the librarian: the ones I worked with were very helpful.

---

### Post by disturbed13 on 2015-01-18
> **amanchesterman said:**
> I don't know where you live, but I am in NW England and I used to teach computing (the basics of browsing, email, wordprocessing etc.) in our local public libraries.

As you say, the machines would sometimes remember data that had been entered in form fields. The librarian told me that it was because users did not properly log out of their sessions when they finished: they would go to a website, enter their data to transact their business and then maybe log out of the site, but would then forget to terminate their user session on the machine. (They would just walk away.)

So besides the advice you've been given above, you may want to check whether something similar applies in your case. If in doubt, turn off the machine when you have finished it. (The library machines I used were set to close down and restart automatically once every 24 hours, to ensure that all user-entered data were cleared.) Ask the librarian: the ones I worked with were very helpful.

well it wasnt my data, but now my rampant paranoia has kicked in and i want safe data transmission from anywhere. so thats why i am really focused on getting a live distro so i can control all of that.

the mini ISO looks like the best way to go i will take that forward. hopefully i can boot from USB on the host machine.

---

