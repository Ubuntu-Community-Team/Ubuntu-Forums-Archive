---
title: "Virus in Linux?"
date: 2015-08-05
forum: General Help
---

### Post by TRAPKTHOS on 2015-08-05
Hi,

I have an old Toshiba Satellite computer that is normally used by a relative (with low IT knowledge) for surfing the Internet.

The O.S. installed in that computer is the Lubuntu 12.04 distribution. All has been perfectly working for several years but yesterday the internet connection (wired) suddenly began to fail while my relative was visiting normal webpages (E-bay, etc.). He asked for my help I and began to try things in order to figure out what was happening.

Suddenly, a strange screen (first time I see this screen in this computer) with a flame and a decreasing status bar appeared in the computer (especially when we change from one user profile to another; pics at the end of this post). It also appears a weird message about authentication via PAM (?). It´s all very strange. The question is that this is supposed to be a screensaver but in the settings option of the PC the current option by default is: only put the screen in black colour.

Is this normal? Is it a virus? As I say ...it´s all very strange for me although maybe it´s a nonsense. 
I
Sorry if I´m saying or asking something stupid...but I´m not a Linux expert. I try to do my best but this time I need help.

Thanks in advance for the info.

Regards.

---

### Post by dino99 on 2015-08-05
Looks like the password is missing / not accepted for some reason
and its related (at first glance) to xscreensaver: so try to purge the installed one, from a terminal or vte (ctrl+alt+f2): > sudo apt-get purge xscreensaver*
Then watch the logs to find something usefull (warnings/errors) that explain that issue (inside /var/log/dmesg mainly and Xorg.0.log)

If your system is updated/upgraded, then it get the security fixes to avoid possible attacks

---

### Post by mörgæs on 2015-08-05
Lubuntu 12.04 is out of support so with this one you can't be secure against malware. Better to do a fresh install of 14.04.2 (or 14.04.3 in a few days) or 15.04.

---

### Post by Topsiho on 2015-08-05
Installing an LTS version is to be preferred, as LTS is supported during 5 years, with using point versions to prevent huge updates. So, according to  mörgæs, 14.04.3 point version will come out in a few days, you better wait for that one.

It seems to me that your Toshiba is a Satellite A50 laptop, I have one (10 years old) that runs Lubuntu quite well, but has a not reliable DVD player, and doesn't boot from USB :)

"Viruses" in Linux nearly always mean broken hardware or software. I don't use screensavers, as many of them (very old, and possibly dated,  experience of mine) are wacky.

Topsiho

---

### Post by buzzingrobot on 2015-08-05
Since it hasn't been specifically stated, No, that's not a virus. That's Xscreensaver, an old screen saver still in use some places. For some reason, it launched when you switched profiles. (Most likely because it was included as a default in that profile.)

---

### Post by RobGoss on 2015-08-05
I've seen this before on my desktop a while and I assure you it's not a virus.

---

### Post by TRAPKTHOS on 2015-08-05
Thanks to all of you for your fast answers.
As I´ve said in my previous message I have a basic knowledge of Linux (this is due to the fact that I normally use Windows ):P. Yeaah!!! I´m sorry :lolflag:) . So:

@dino99

The system is not updated because I deactivated the updates in order to avoid my relative messages related to new versions, etc.
Furthermore, I´m not very used to dealing with the terminal and if I have to look for erros / warnings in logs I think it will be better to do a fresh / clean installation. In fact, the computer is empty (there are no personal files, documents, etc.) 

@mörgaes

Thanks for letting me know that this version is outdated. Now that  I have decided to do a fresh installation I will install 14.04.3 or 15.04.

@Topsiho

In fact it´s a Toshiba SA80-131. Quite old. That´s why I installed Lubuntu on it..and since then, at least, it works for basic Internet navigation. The DVD player still works and I´m not sure now but I would say that this model can boot from a USB pendrive.

@buzzingrobot & @RobGoss

Thanks both of you for confirming that it´s not a virus and your possible explanation about why this can be happening. The question is that the image of the flame is quite terrifying. That´s why I thought maybe it was a virus / malware... Although all we know there are no viruses for Linux ;-)  ...of course.

Thanks a lot for your help, guys!!!

Regards.

---

### Post by mörgæs on 2015-08-06
> **TRAPKTHOS said:**
> 
The system is not updated because I deactivated the updates in order to avoid to my relative messages related to new versions, etc.

Then you are putting the users at risk. A system which is not updated should be considered a security breach.
Better to let updates take place in the background so the user does not have to deal with them.

---

### Post by TRAPKTHOS on 2015-08-06
Yes, I know that in normal conditions it´s not a good strategy.

But this user only surfs the Internet. He doesn´t enter passwords in webpages (Amazon, E-bay, forums...neither e-mail or bank accounts).

That´s why I decided to deactivate the updates of the system.

Anyway, thanks a lot for your warning.

Regards.

---

### Post by buzzingrobot on 2015-08-06
> **TRAPKTHOS said:**
> 

But this user only surfs the Internet. He doesn´t enter passwords in webpages (Amazon, E-bay, forums...neither e-mail or bank accounts).




Be aware that there are malware packages in use that are activated simply by opening a page in a browser. Linux is not immune to malware. It's just not nearly popular enough to be an attractive attack alternative to Windows.

---

### Post by TRAPKTHOS on 2015-08-06
Yes, I know almost all the current threats: virus, worms, trojans, malware, crapware, spyware, ransomware, roguewares, SCRIPTS (what you are referring to), RATs, APTs, infections using legal ads of webpages, etc.

But, what I´m trying to convey is that only in the particular case of this old computer, with such a low and particular kind of use (not used for accessing to general services which require a username and a password), if the machine suffers an infection the solution would be very easy: reinstalling the OS (the PC is empty with no documents, no photos, no passwords stored on it, etc.). For me this is more easy than the fact of having to update the software during all the year. 

The other 2 computers I own (Core i7) are highly secured with:

A Firewall
An Updated paid antivirus
Java, Flash, O.S, Browsers and main programs updated to the last patches / versions
Used with Standard accounts (low privileges)

**Anyway, thanks a lot for being so worried about the security of my old system. Highly appreciated.**

Regards from Spain- EU.

---

### Post by Topsiho on 2015-08-06
I am not quite sure, but I think that a chain is as strong as it's weakest link: having an insecure computer in your network, may put the other computers in that network at risk.

Also: daily updating your Ubuntu computer is quite easy and fast, incomparable to the fuzz and misery of the monthly Windows updates. Due to the large number of very fast and up-to-date mirror sites all over the world.
Also: having a fully updated system makes installing new applications a cinch, as dependencies are met.
I use Ubuntu from day one in 2004 (and fell in love with it immediately, head over heels, after my many adventures with other Linuxes before that time :) . For a large part because of the updates, and the escape from the dependency hell because of that). In all that time only one update went wrong: in 2006. This misfired update was fixed the next day. So the risk of updating Ubuntu is very small.

Linux is not safe because of a lack of popularity. It is far more used, on far more important systems, than Windows, only not so on the desktop, which is fine.
And in servers that are badly managed it proves to be vulnerable also :( (no or bad passwords, no updates, bad firewalls, unreliable software, unnecessary/bloat software, such as desktops).
Unfortunately, Android is a farce. Based on a Linux kernel, it is spyware. I hope, but don't know, that this is better in the Ubuntu phone?

Topsiho

---

### Post by TRAPKTHOS on 2015-08-10
>  I am not quite sure, but I think that a chain is as strong as it's  weakest link: having an insecure computer in your network, may put the  other computers in that network at risk. 


I have my wifi with a WPA2 password, my router with a strong, non-dictionary and long password, I use MAC filtering, I have an Internet Security Suite  (including Antivirus, Two-way firewall, Network Attack Blocker, etc.). I use programs like Malwarebytes, Adwcleaner, Spywareblaster, Antiransom, Cryptoprevent... I use plugins like No-script, Ad-block, Ghostery...I avoid all the crapware while pressing next, next, next...during the setup process of the different programs...and maaaaaaaaaany other security measures.

But... I must confess that I can't refute what you say because, in fact and to be honest, I know you're right (:oops::oops::oops:).**_  And I know it because I have sometimes thought about this question too_**. I mean, could  somebody attack my network using as an access point the computer with  the lower protection? I suppose it would be quite improbable but not  impossible. That's why I have always believed that this was  the weak  point of my infrastructure (like you say in your post).

Now that you have said it to me too, it has been like: OK, I was not being paranoid with the security...I was right!

I think it's time to take into account the installation of the last version of Lubuntu **and keep it up-to-date.**

Thanks a lot for your piece of advice. It has been food for thought :D.

Regards.

---

### Post by Topsiho on 2015-08-10
:)

Topsiho

---

