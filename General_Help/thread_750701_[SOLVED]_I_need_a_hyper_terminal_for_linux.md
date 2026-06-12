---
title: "[SOLVED] I need a hyper terminal for linux"
date: 2008-04-09
forum: General Help
---

### Post by kdarkentity on 2008-04-09
What is a good hyper-terminal like program for linux?

---

### Post by p_quarles on 2008-04-09
Can you add a little more information explaining what you mean? The only thing I remember going under that name was the Win 9X modem dialling software. Beyond that, "hyper terminal" doesn't mean anything special to me, but it's quite possible that I or others know of applications that will accomplish what you are looking to do.

---

### Post by y-lee on 2008-04-09
I'm with p_quarles on this, I  don't know exactly what ya mean either. Maybe [Putty ]("http://en.wikipedia.org/wiki/PuTTY")is something like what ya are referring to. i ssay that after googling [hyper terminal]("http://technet2.microsoft.com/windowsserver/en/library/02c2459f-5b84-45fb-afab-610374d359941033.mspx?mfr=true"). I use neither program so am not sure exactly what they are capable of. I did however install putty on a ubuntu machine for a relative  who like to play muds.

---

### Post by p_quarles on 2008-04-09
> **y-lee said:**
> I'm with p_quarles on this, I  don't know exactly what ya mean either. Maybe [Putty ]("http://en.wikipedia.org/wiki/PuTTY")is something like what ya are referring to. i ssay that after googling [hyper terminal]("http://technet2.microsoft.com/windowsserver/en/library/02c2459f-5b84-45fb-afab-610374d359941033.mspx?mfr=true"). I use neither program so am not sure exactly what they are capable of. I did however install putty on a ubuntu machine for a relative  who like to play muds.
PuTTY is definitely similar to the Windows hyper terminal, but all if its functionality is built into the default Ubuntu shell anyway. PuTTY won't do anything that a simple ssh or telnet command won't do.

---

### Post by y-lee on 2008-04-09
> **p_quarles said:**
> PuTTY is definitely similar to the Windows hyper terminal, but all if its functionality is built into the default Ubuntu shell anyway. PuTTY won't do anything that a simple ssh or telnet command won't do.

I agree with that :) Putty is just easier for people scared of CLI once it is set up to do what they wish to do with it.

---

### Post by stinger30au on 2008-04-09
this may help

[http://www.strdoc.net/hyperterminal-replacement-ubuntu-minicom](http://www.strdoc.net/hyperterminal-replacement-ubuntu-minicom)

 was kinda surprise that **HyperTerminal** is not available anymore in Windows Vista. No problem, I rebooted my notebook to Ubuntu and fire-up **minicom**. [LIST=1]
[*]By default, minicom is not installed in Ubuntu, so you need to install it first.
 sudo apt-get install minicom
[*]Find the name of your Serial Port
dmesg | grep tty
In the output look for something like "tty". The output in my case is like this:
$ dmesg | grep tty
[   17.341823] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.342454] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
This means the device correspond to my serial port is *ttyS0*.
[*]Configure minicom
sudo minicom -s[LIST]
[*]Use the keyboard keys to select the menu item *Serial port setup*.
[*]Enter A to change the *Serial Device* to */dev/ttyS0*, and then enter E to change the line speed to 9600 8N1
[*]Using arrow keys, select *Save setup as dfl*[/LIST] 
[*]Select *Exit from Minicom*.
[*]Next time, from the terminal you only need to run sudo minicom in order to access your Cisco box.[/LIST]

---

### Post by _aXXe_ on 2008-04-10
I'd like a good GUI Hyper Terminal substitute for Gusty also. I would like to revisit some of the old ANSI BBS's via the internet. I'd like to use something simple as I don't need a lot of bells and whistles.

I'd also like to use my Excalibur GUI BBS terminal in Ubuntu. Does anyone know a way to set up a 16 bit Windows program using Wine or an equivalent program? I need to have access to my Excalibur BBS and would like to use my Ubuntu PC instead of running to the other room to use a Windows box.

Thanks.

---

### Post by Rhubarb on 2008-04-10
If it's a serial port you want to access, then there is a nicer gui alternative to minicom:
```
sudo aptitude install gtkterm
```
gtkterm allows you to connect to serial modems / other serial devices easily.
It works with standard serial ports and USB to serial ports.
Once installed, you'll find it in Applications --> Accessories --> Serial port terminal

---

### Post by aelric on 2008-04-10
I have same issue, don't really care if it is gui or not. I just need to know how to conect to a switch via the serial port on my ubuntu laptop. 

I've tried installing minicom 2.3 and it won't compile. I have also tried the sudo apt-get gkterm as well as sudo apt-get minicom, both reply with could not find package.

:confused:

---

### Post by Rhubarb on 2008-04-10
> **aelric said:**
> I've tried installing minicom 2.3 and it won't compile. I have also tried the sudo apt-get gkterm as well as sudo apt-get minicom, both reply with could not find package.
Try putting the **t** in g**t**kterm
You obviously need to be connected to the internet to get these packages.

---

### Post by aelric on 2008-04-10
thanks got sorted on minicom eventually.

---

### Post by kdarkentity on 2008-04-10
Thanks guys i'm all set.

---

### Post by _aXXe_ on 2008-04-17
I still need a GUI program to connect through the NIC for access to Internet ANSI BBS systems. I used the hyper-terminal (Windows) for years and I liked the product enough to buy it. Yes, I know that the BBS is passe' to many but I still like to chat and upload files.
I run a GUI Windows BBS and I look for files that fit my BBS's format. I still have many 180, 360, 720 and 144 floppies with old DOS programs that I trade for extended download access.

I'm not interested in accessing my network PC's or server.

Thanks

---

### Post by y-lee on 2008-04-17
> **_aXXe_ said:**
> I still need a GUI program to connect through the NIC for access to Internet ANSI BBS systems. I used the hyper-terminal (Windows) for years and I liked the product enough to buy it. Yes, I know that the BBS is passe' to many but I still like to chat and upload files.
I run a GUI Windows BBS and I look for files that fit my BBS's format. I still have many 180, 360, 720 and 144 floppies with old DOS programs that I trade for extended download access.

I'm not interested in accessing my network PC's or server.

Thanks

Maybe[ qterm]("http://qterm.sourceforge.net/wiki/index.php/Main_Page")

[SyncTerm]("http://syncterm.net/") looks good too but it is a terminal app

---

