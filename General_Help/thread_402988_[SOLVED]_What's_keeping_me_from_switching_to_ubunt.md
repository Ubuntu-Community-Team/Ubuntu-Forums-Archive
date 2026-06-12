---
title: "[SOLVED] What's keeping me from switching to ubuntu.. (USB modem)"
date: 2007-04-06
forum: General Help
---

### Post by nowshining on 2007-04-06
one thing holding me back and that is the lack of USB support for my Actiontec  USB/SERIAL modem, then i'd switch, also I have to say I have PHYSICAL proof MS, makes HArdware upgrades a requirement, and that is that I have an older monitor won't work on this computer but it will, that's right, if I use it while I have XP it will go awry and the screen will mess up, however here's the thing, I tried one time to test it out with Ubuntu to see if it was my computer or not, I input the live CD (old one I get them sent to me so I am one step back- and I am on dialup)... and guess what, that's right it worked just fine, I could move the mouse, the Desktop was clear, etc... AND THIS ONE THE SAME COMPUTER AND SUCH... by the way administrators can copy that part and input it into testimonials if like...

---

### Post by tgm4883 on 2007-04-06
Sounds like a driver issue to me.

I know this isn't exactly what you were looking for but call your isp and see if they have an ethernet modem.  I thought I read somewhere that they had to have at the least ethernet modems (in the US that is)

---

### Post by Brunellus on 2007-04-06
USB modem support in linux is terrible.  

The easiest way around this is to spend a few bucks and get a supported modem.  There are still old-style serial modems that are wholly linux supported.  

What I understand LEAST of all is the stubborn insistence of so many users on ADSL modems that use USB.  Why?  Spend a few bucks and get one that speaks real ethernet.  I don't understand why anyone would want to use USB for networking if he already has ethernet.

---

### Post by lukew on 2007-04-06
> **nowshining said:**
> one thing holding me back and that is the lack of USB support for my Actiontec  USB/SERIAL modem, then i'd switch, also I have to say I have PHYSICAL proof MS, makes HArdware upgrades a requirement, and that is that I have an older monitor won't work on this computer but it will, that's right, if I use it while I have XP it will go awry and the screen will mess up, however here's the thing, I tried one time to test it out with Ubuntu to see if it was my computer or not, I input the live CD (old one I get them sent to me so I am one step back- and I am on dialup)... and guess what, that's right it worked just fine, I could move the mouse, the Desktop was clear, etc... AND THIS ONE THE SAME COMPUTER AND SUCH... by the way administrators can copy that part and input it into testimonials if like...

Sorry for sounding thick but usb/serial modem? That sounds like a dial up modem? Linux does not( used not to ) support win modems (feal i am going to be corrected here but the only time I tried to get a win modem to work under linux was about 8 years ago and it was always a big no no ). Is it a win modem?

Is this a asdl modem or a dial up modem?

I agree with the other bloke; only a few pounds to get a supported modem. I know having to buy around certain makes is a pain; but sometimes trying to get a piece of hardware to work for ages is more of a pain than shelling out a few pounds.

---

### Post by aysiu on 2007-04-06
I've moved this to the support forums so you can get some proper help.

---

### Post by Valstorm2323 on 2007-04-06
Well I spent 3 days getting my Speedtouch 330 THOMSON USB ADSL to connect through Ubuntu. 

IT was a  learning experience and now that I look back, it wasn't that hard. Sure you need to enter commands in the terminal window but ehhh something to get used to.

---

### Post by aysiu on 2007-04-07
Mind posting a link to what helped you out, in case someone with the same model stumbles upon this thread?

---

### Post by Valstorm2323 on 2007-04-07
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

that's the link I used, it's not much different from the ubuntu one. 

Only thing people have to bear in mind is the SUDO command in the terminal, making sure their files are in the FOLDER they created being in the folder through the terminal.

Once they've done all that's stated in that link, reboot computer run this command in terminal to see if ADSL is up and running tail -f /var/log/messages

If it is then the next command will officially connect them> sudo pppd call speed touch

At least that's how I got through it.

One mistake I made and think others have is that we all try to get the files to be compiled instead of just getting the file with the pure code.  It's the one that shows up as nothing but code when you press the link. You have to save that one.

Next mistake I made was not having identical username in the files I had to create. If the name isn't EXACTLY the same in the secrets and speedtch file then you'll have to adjust it.

---

### Post by nowshining on 2007-04-14
it is an external dialup modem. I have only one com port on the computer I have and that is used for syching my palm IIIxe the modem is like I said usb/serial and I heard about the linux unsupport problem with winmodems. I use Juno free ten hour service by the way. And thanks for ur help, I will retry the next version that is available for free shipping to my house, I know again one version behind, by the way if anyone has anymore ideas please continue. oh and if I can't get this working, via usb, I am going to abandon 
ubuntu linux, however I won't be upgrading from xp sp2 pro to vista.

The shopping.com page says cable modem, however it's not correct, because in the picture you can see the phone cable anyway that is it.
& No I didn't get it thru AOL, I got it from tigerdirect.com which at the time with shipping and handling was cheaper than geeks.com
 also tiger didn't add no sales tax at the time.
EDIT 2:
By the way I dial into juno thru Dialup Networking (DUN) not thru their software. So in the end It's just setting up the same thing with ubuntu,etc.. as I think I can manage that, it's the getting the modem to work that I need. 

[http://www1.shopping.com/xPO-Actiontec-Actiontec-Modem-Kit-from-AOL](http://www1.shopping.com/xPO-Actiontec-Actiontec-Modem-Kit-from-AOL)

---

