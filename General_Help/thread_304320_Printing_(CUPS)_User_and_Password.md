---
title: "Printing (CUPS) User and Password"
date: 2006-11-21
forum: General Help
---

### Post by r.cannell on 2006-11-21
Whenever I try do do certain things in CUPS I am promted for for my "username and password for CUPS at http://localhost:631/printers" . 

I enter the ones I use to log onto the computer (I am the only user) and get the same prompt again. Entering the same username and password a second time still does not work but the prompt does not reappear.

Any advice gratefully received.

Thanks
Rob

---

### Post by ranatanveer on 2006-11-28
I am also facing the same problem. while connecting to [http://localhost:631/admin](http://localhost:631/admin) it ask password. i tried all my passwords. root and sudo users even but the username password windows appears again and again. what to do for that problem. i am facing this problem even all the distro of ubuntu. 5.04 6.06 etc.

---

### Post by fragos on 2006-11-28
I just tried [http://localhost:631/admin](http://localhost:631/admin) on Ubuntu 6.10 and tried changing from the color cartrige to the grayscale on my PSC 1410.  It prompted for ID, PW and I used my Ubuntu user name and PW which was accepted.  I seem to remember this not working before but now it dose.  I added my printer before with System-> Administration-> Printing.

---

### Post by a.d.gardiner on 2006-11-29
Ok,

this might not work,but I did the following to fix Xubuntu, I imagine Ubuntu/Kubuntu are the same. I just re-checked the manual and did this DUH!:

1) Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups

2) Select the group shadow and click Properties.

3) Add the user cupsys to the group.

4) Restart CUPS with this command:
```

$sudo /etc/init.d/cupsys restart

```

5)Access CUPS web based configuration console thing at [http://localhost:631/admin](http://localhost:631/admin) and it won't ask for a password or username to add/remove printers.

When adding my printer I loaded the HP1200 PPD instead of using the built in driver (I think you need the PPD file, like a printer driver it seems).

I got mine from linxprinting.org (I think they have most other printers there too) and it worked. CUPS now no longer asks for a password and I could correctly configure my printer. Only thing is it won't print centered! lol

Hope it helps :)

---

### Post by r.cannell on 2006-11-29
I did as you said and  it still asks me for a password but now it accepts the ones I give it. To me, that counts as a success!
I had also been playind around with the /etc/cups/cupsd.conf file - commenting out lines that I thought might be asking for passwords. I hadn't succeeded but was trying just a bit at a time - maybe I could have done it eventually.

Thanks for your help.

PS The restart command wouldn't work, I had to reboot. Is the path different for Dapper?

---

### Post by ranatanveer on 2006-12-11
I have read the documentation and if we comment out these lines in cupsd.conf

AuthType Basic
AuthClass User

to

#AuthType Basic
#AuthClass User

it will not ask for username and password.

---

### Post by malel on 2006-12-11
This is exactly the same thing that I encountered with CUPs when I tried to get my printer working . I still don't know what I did but the printer is working okay now . It is a HP PSC 1510. 
Thanks very much for the post I have printed a copy off for future reference.
:)

---

### Post by bluegroper on 2006-12-11
> **malel said:**
> 
Thanks very much for the post I have printed a copy off for future reference.
:)

You can print it now that CUPS is working !:-D

---

### Post by timcredible on 2007-02-21
i tried all these things, and also deleted/re-added the printer.  now, the System->Administration->Printers shows the correct settings, but the printer is still only using the color cartridge, and cups is still asking me for a username and password.  Any ideas?  I'm running 6.06 and have an hp psc 1350 printer.  Thanks.

---

### Post by timcredible on 2007-02-26
found a solution - installed a new version of hplip from sourceforge.  followed directions on sourceforge, and not only can i change the printing parameters, hp-toolbox now works also.

---

### Post by olafant on 2007-09-09
The unrecognised password on localhost prompt still occurs in Gutsy T5

The solution for me on Feisty and Gutsy is to make sure that you as a user are in the lpadmin group by going to:

System
Users and Groups
Manage Groups
lpadmin Properties

and ticking yourself as a member of the group

Going direct to the cups server elicits the same response so that is where the permissions issue appears to manifest 


Regards

---

### Post by keyboardashtray on 2007-10-30
> **olafant said:**
> The unrecognised password on localhost prompt still occurs in Gutsy T5

The solution for me on Feisty and Gutsy is to make sure that you as a user are in the lpadmin group by going to:

System
Users and Groups
Manage Groups
lpadmin Properties

and ticking yourself as a member of the group

Going direct to the cups server elicits the same response so that is where the permissions issue appears to manifest 


Regards

Thank you olafant! That worked for me! :)

---

### Post by rare HERO on 2008-02-22
Worked great.

---

