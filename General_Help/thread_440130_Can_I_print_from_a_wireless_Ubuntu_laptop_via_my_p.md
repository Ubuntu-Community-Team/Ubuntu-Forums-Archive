---
title: "Can I print from a wireless Ubuntu laptop via my printer connected to XP computer?"
date: 2007-05-11
forum: General Help
---

### Post by alanmzifa on 2007-05-11
I've been trying to search the forums and Community docs for some information on how to set up my Ubuntu 6.06 laptop to share a printer. 
So far I've found information that allows a windows machine to share with an XP machine **but mine will need to be set up differently.**
I imagine this question has been asked and answered before but I can't find anything through the searches which has this set-up.

[B]The XP machine has a wireless connection to my router, no wired connection.
It is connected via USB to the HP7210 printer.
My laptop uses Ubuntu 6.06 and has a working wireless connection to the router, no wired connection.[/B]

I want to be able to hit "print" when on the wireless Ubuntu laptop (wherever the user happens to be in the house) and and have the printer (which is in a home office) print the relevant document from the printer connected to the XP desktop box.


Firstly, with this configuration is it possible to do this?

Secondly, how do I do it? What do I need to do on both machines and in what order?


I'm fairly new to Linux although comfortable with my way around Windows, so I need any instructions to be written in "idiot". Perhaps "semi-idiot".

Thanks in advance.

---

### Post by louieb on 2007-05-11
I do just that. HP7660 printer hooked up to old Acer laptop running XP, Wireless connection to router. 
I have Various PCs running XP and/or Linux, wired and wireless, all go through the router for  internet access and file/printer sharing.
The short of it:
Set up a workgroup on your windows machines.
In XP: Set the printer up as shared network printer.
In Ubuntu System>Administration>Printing>Add Printer
Tell it you want a network printer just follow the prompts it should find you windows printer.  If it gives you a recommenced drive your done just click next and your done.

---

### Post by NilsE on 2007-05-11
It is actually pretty straight forward and works. I have my laptop on wireless at home and a Dell printer plugged into an old laptop WITH xp that is also wireless. FYI I use the old laptop as a print and file server only.

Anyway, you have to first go into Windows and permit sharing then go into the printer properties and allow sharing for it and give it a name (mine is DellPrinter)

In Ubuntu go into printing and select "add printer" then follow the prompls and go With the option for a printer on a workstation on the same netwok. It may detect it but worst case you have to give it the name of the PC and the name of the printer. Mine is Home and DellPrinter.

The only problem you may have is finding a driver for the printer in Ubuntu.  My Dell has no drivers so I just went with a Lexmark postscript driver and it worked.

---

### Post by alanmzifa on 2007-05-11
I've tried what was in the 2 previous replies but no luck. Although printer appears installed on the Ubuntu laptop when I print a test page nothing happens. 
I've tried installing and re-installing several times.

When I'm asked on the Ubuntu machine for information (in step 1 of the printer set-up) I don't know what I should be entering in the relevant boxes.

My Windows workgroup is called ***MSHOMEWORK***.
The Windows computer is named ***officepc***.

Here's a dailogue of what happens...

Open Printers.
Add a printer
**Step 1 of 3** , **printer connection**
A small window called **Gnome Cups add** pops up then disappears.
I select **Network Printer** and **Windows Printer(SMB)** from the 4 options.I get **Host** , **Printer** , **Username** and **Password** boxes opening and almost simultaneously an **Authentication Required** window opening up asking for **Identity** and **Password** for **MSHOME** (note NOT MSHOMEWORK  ??).
I type my Windows log-in password in the empty box (my user name is already pre filled) and click the **Connect** button.

That window disappears and pre fills the **Username** and **Password** boxes but I don't know what to enter in the **Host** and **Printer** boxes. I've tried several options and although when completed with something the **Forward ** button lights up and allows me carry on I can't help thinking this is where the process is breaking down, perhaps because the info for** Host** and **Printer** is wrong.

I can fill in **step 2** and again I guess at what should go in the dialogue boxes for **step 3** before clicking **apply**.

[I]I don't know what I should be putting in each of these boxes or where I get the correct text/names to enter in each. 

Perhaps someone could help clarify? [/I]

thanks

---

### Post by louieb on 2007-05-11
> **alanmzifa said:**
> 

Open Printers.
Add a printer
 **Identity** and **Password** for **MSHOME** (note NOT MSHOMEWORK  ??).
I type my Windows log-in password in the empty box (my user name is already pre filled) and click the **Connect** button.
That the first problem my authentication window correctly has my workgroup name. I enter my printer computer user name there (don't have a password)

Double check the workgroup name on the print server.  
> 
That window disappears and pre fills the **Username** and **Password** boxes but I don't know what to enter in the **Host** and **Printer** boxes.After the authentication window  the host box have drop down list that list the computers on the network.   I click on the computer w/the printer. 
Then click on the printer dropdown and the printer share name is listed. I click on it.

So I guess you next step is to check your window workgroup settings.

---

### Post by alanmzifa on 2007-05-11
Louieb , thanks for replying again. 

I'm not clear on what you wrote. Can you spell (or anyone else) it out for me?

*"I enter my printer computer user name there (don't have a password)"*
Do you mean you enter your username or computer name or printer name? And is "there" the authentication box or the Step1, add a printer box?



and..

*"So I guess you next step is to check your window workgroup settings."*
How do I do that please?


thanks

---

### Post by louieb on 2007-05-11
Well I had to hunt around XP but to check workgroup name Right click on my computer > properties> Computer name tab. 

Your XP machine has users. go to the control panel > user accounts you will see the names of the user(s).  Thats the name you want for the printer setup in Linux.

---

### Post by Staff Monkey on 2007-05-11
There's another option that you can try:  

  By entering the workgroup name and the name of the host, you are (in essence) relying on Windows and Ubuntu to mutually agree on what computers are assigned to which IP addresses.  You can bypass this by replacing the host name of the computer with the printer to the ip address.

WARNING: Since many routers are configured for DHCP, this can change.  If this method is your permanent method, I recommend disabling DHCP.

---

### Post by alanmzifa on 2007-05-11
Well, I've got the printer partly working. Thanks. Here's what I did.


I uninstalled Samba as I've seen posts that said it wasn't necessary.

Then  added the printer setting the connection as host = 192.168.0.2, Printer = HPOffice

Then I went to HPLIP and set that up in the CUPS interface.The CUPS  interface won't let me change any settings, it asks for username and password but just keeps popping the box up again every time I enter them.



But..... currently I seem to have very few options when I print, I can adjust margin size but that's about it. 
How do I get to be able to print 2 sheets to page, mono etc. ?
Also, Shouldn't HP device manager (HPLIP) be able to see the printer? It says it doesn't.


It's 2.30 am here. I'll catch up with any replies in the morning.

Thanks again

---

### Post by alanmzifa on 2007-05-12
sorry, jump bumping as I haven't been able to get  HPLIP sorted.

I'd appreciate any words of wisdom.

thanks

---

### Post by alanmzifa on 2007-05-12
I've managed to get the printer printing wirelessly by setting it up through the Windows machine (which is where the printer is connected to) by selecting **network printer** and **windows (SMB)**.

It appears I can't set the printer up to use HPLIP through the wireless connection, the latest version of which I've downloaded and installed.

When I print a multi-page document I only have access to the dialogue windows **shown below** which don't appear to give me the option to **print in reverse order** so all my documents print in the order page 1, then 2, 3 etc which means page 3 is on top followed by 2, 1.

**How do I set the printer to always print in reverse order through Ubuntu?**

---

### Post by louieb on 2007-05-12
Other that a bump not much help here. Just looked. Reverse printing is not an option on my setup either.

---

