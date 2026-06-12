---
title: "Windows Printing"
date: 2008-04-16
forum: General Help
---

### Post by herbie643 on 2008-04-16
I have a Windows XP Pro computer and have installed Ubuntu on another...  Everything is fine so far.   However, when I try to Add Printer on the XP box all I get is the Ubuntu computer.. No printer.  The printer has been installed on the Ubuntu computer and works fine.
The printer is shared by the way.
Any ideas.

---

### Post by .nedberg on 2008-04-16
On the windows machen browse to \\ubuntumachine (just replace ubuntumachine with the hostname of your ubuntu machine)

You should see "Printers and faxes", double click this item and select your printer.

Did you share it with samba?

Also, have a look at this: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by nicedude on 2008-04-16
Assuming you mean you have a printer connected to your ubuntu 7.10 box and this box is networked to your second PC which is running Microscum XP Pro, and that when you try to use the XP control panel -> printers and faxes -> add a printer -> network printer -> browse - and at this point all you see is Ubuntu system but no printer listed. If thats your situation I believe this is your solution.   

1) Make sure your printer is installed.
2) Open the Printing window in ubuntu (System -> Administration -> Printing).
3) Click Server Settings in the list of printers.
4) To the right, under Basic Server Settings, check the box that reads, "Share published printers connected to this system".
5) In the list of printers, click the printer you want to share.
6) Click in the Policies tab and make sure all three check boxes (Enabled, Accepting jobs, and Shared) are checked.
7) Click the Apply button in the lower-right corner of the window.

Then on the Windows machine:

1) Now add the printer to the Windows computer by using the Windows "Add Printer" Wizard. Select to connect a network printer and then select the option to connect a printer on the Internet or on a home or small office network. Type in the following for the printer URL:

http://<hostname>:631/printers/<printername>

Replace "<hostname>" with the hostname of the Ubuntu computer sharing the printer. It's also possible to replace "<hostname>" with the IP address of the computer sharing the printer.

Replace "<printername>" with the name (exactly as displayed including displayed casing) that was shown in the Printers window you opened earlier on the Ubuntu machine. If you're unsure about the exact printer name, you can use your webbrowser to open

http://<hostname>:631/printers/

That should show your printer in a webpage. Click on your printer link, and you should see the exact URL in your browser's address bar. You can use that URL in the Windows setup mentionned above.

2) Windows will ask you to select a driver for the printer. If you have the Windows print drivers, you should use them. Click the "Have Disk" button and select the .inf file that describes your print drivers.

If you do not have the drivers for the printer or cannot load the .inf file, you should select the "MS Publisher Color Printer" driver from the "Generic" manufacturer. This driver should be found on all Windows 2000 and XP installations by default and it gives all the printing functionality one should need. 

Found that tip in the forums for ya. hope that gets you all fixed, if I misread your setup then post back with a detailed description of your network configuration, printer model and printer connection type your using and ill try again. You make me jealous though as my printer is a paperweight in Linux which forces me to dual boot with XP Pro so I can still use it :-(

---

### Post by herbie643 on 2008-04-16
Nedberg;
So far so good..  Thanks so much.. really helped a lot.

---

### Post by herbie643 on 2008-04-16
NiceDude;
All worked fine..  Sorry to hear that your printer doesnt work.  My HP is almost 4 yrs old.  So perhaps thats why it works.  Maybe?
Thanks again for all your help.

---

### Post by .nedberg on 2008-04-17
I heard that HP printers generally works fine. At least all my HP's do. Canon printers are problematic, some work fine, some don't. Lexmarks might not work. At least that is what I read somewhere on the net.

I only buy HP printers because of this and never had a problem!

---

### Post by nicedude on 2008-04-17
HP is better than lexmark but I was just unlucky that when I finally decided to make the switch to Ubuntu I had recently got a all-in-one lexmark printer. Basically you should watch out for any all-in-one scanner-fax-printers as they are generally not supported. I guess it would be to much work for them to actually make a linux driver and it might upset the evil Redmond Washington crew to be seen not serving their monopoly exclusively LOL. well tomorrow I am switching my 80 year old grandma's PC from XP to linux since she's got a virus situation, So another PC will be switching from the dark side to the rebel alliance. Every PC I switch I get a good feeling inside, never got that feeling throwing XP on boxes.
Glad you got your situation fixed up.

---

