---
title: "How do I (simply) share a printer connected to an XP machine?"
date: 2007-08-07
forum: General Help
---

### Post by alanmzifa on 2007-08-07
Recently I've changed router and re-installed XP on my main desktop PC with Ubuntu running on my laptop which my 3 yr old uses.
[B]Both connect wirelessly to an ADSL router. 
My printer is connected via USB to my XP machine. The laptop resides in a different room.[/B]

I had managed to get my Ubuntu laptop to print through the Windows machine before I wiped and re-installed Windows and changed router but have forgotten how I managed it. I need some help configuring this again in simple terms. 
**I know I didn't install Samba but set it up somehow with the CUPS interface and the HPLIP utility for HP printers.**

I've searched here and the web but nothing I''ve found makes complete sense to me either because it uses Samba or because it doesn't tell me exactly what dropdowns and addresses I should be using in CUPS. 
I spent a few hours on this yesterday trying different options but although the laptop appeared to have the printer installed I couldn't get anything to print so I must have been doing something wrong.
[B]
Could some of you please help me to get this up and running again?[/B]

thanks

---

### Post by NoSmokingBandit on 2007-08-07
Samba is the easiest way to set it up. It took me about 5 minutes for my network at home. There a ton of guides around that tell you how to do it, just google "samba configure" or something like that.

---

### Post by alanmzifa on 2007-08-07
Thanks for your reply but I'd rather avoid Samba if possible. 
The only Samba related how-tos I've seen here omit the same type of detail I mentioned in my first post. I'm pretty sure I didn't need to touch the Terminal last time I set up printer sharing or use Samba.

I've also read on this forum that I shouldn't need Samba just to print via an XP machine.

Can anyone help?

---

### Post by rax_m on 2007-08-07
I've set up printing to my XP machine in another room, only difference is that it's a desktop connected via a LAN card. Had to do the following :

1. Share the printer in XP 
2. Ensure that your Ubuntu box can get thru your (Windows) firewall  to the XP box
3. Go to System -> Admin -> Printing
4. Select Add new NETWORK printer
5. Select the Windows (SMB) printer and enter all of the details. 
6. Print a test page and it should work

Hope that helps.

Cheers
Rax

---

### Post by alanmzifa on 2007-08-07
thanks for your reply.

[B]I always fall down on even simple instuctions like this because of something I don't know.

I don't know what I'm supposed to put in these boxes.[/B]


When I select **Network Printer** as you described I get a dropdown with 4 choices. Although I don't have Samba installed you say select **Windows SMB **(not CUPS?).
I then get 4 fields to fill in...

**Hostname  **                        presumably **192.168.1.34**, the IP of the XP box
**Printer   **                             presumably any name I want to call the printer
**Username **                         don't know
**Password **                         don't know

I've tried (don't laugh) my Ubuntu login for username and password. They don't work. Tooltip on box suggests ***usernameDOMAIN/username***. Unfortunately I don't know what that means.
[B]
Can you (or anyone who reads this) spell out what I need to fill in in these boxes. [/B]
I currently have my XP desktop firewall turned off until I get this operational.


thanks

---

### Post by lintoon on 2007-08-07
For "Printer" type in the name of the printer assigned in XP.  Start Menu - Control Panel - Printers and Faxes - Right click on your printer and select "Sharing" - Type the name as it appears there.

Username and password is to authenticate you with the XP box so you have to type in the details of a user on the XP box

"Username" - Type in your XP username
"Password" - Type in your XP password

Hope this works.

---

### Post by alanmzifa on 2007-08-07
Thanks lintoon.

I've got it working using what you said.

For the benefit of others (but more likely myself next time I change something and have to set it up again) I did this...

For *hostname* I entered the XP box's IP address **192.168.1.34**.
For *Printer* I entered what I'd labelled the printer in *Sharing printer* on the XP box, **HPOffice**.
For *username* I entered my XP PC name and my XP login name, **OFFICEPC\Monty**.
For *password* I entered nothing as I don't use a password to login on my XP box.
Successfully printed a test page.

Next time I opened the printer properties on the Ubuntu laptop I noticed that the *username* field was empty again. This doesn't appear to make a difference however and leaving it blank next time still resulted in being able to print pages. Same with the XP box's firewall restarted.

Thanks again. Typical of all things in life it's never the big picture that confuses us. It's always the detail.


**Out of interest, is there any disadvantage to setting  the printer up this way as opposed to using the CUPS web interface (the detail of which evaded me anyway)?**

---

### Post by rax_m on 2007-08-08
hey alanmzifa

sorry if I wasn't clear enuf about the userid / passwd thing.. sometimes I  forget that something obvious to one person is not obvious to another ;) 

Glad you've got it working tho. 

As for your last question, I'm afraid I don't know if there are any disadvantages, but I haven't experienced any yet.

---

### Post by lintoon on 2007-08-13
Excellent.  Glad you got it working.  I've been on holiday hence the late reply.

---

### Post by upthelum on 2007-08-13
I'll bookmark this page for a friend, thanks.

---

