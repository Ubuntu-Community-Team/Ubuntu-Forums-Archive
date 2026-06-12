---
title: "Lost wireless connection on Xubuntu"
date: 2012-12-17
forum: General Help
---

### Post by Wuxin on 2012-12-17
The other night I was working on my laptop that has Xubuntu installed.  I was on the internet and had absolutely no trouble.  Later I found I was unable to get online.  I put
my authentication password in but the computer did not respond.  I have since used the internet on my laptop at public wifi hotspots and it works fine, so I know it's not the internet itself.  What do you suggest to get my wireless capability working again at home.  For some reason my computer is not responding to my router.  Any advice will be appreciated!

---

### Post by slixz85 on 2012-12-17
we need some more info about this. how long has it been doing it. if you posted this immediately it could begin to work again it does this at my house as well sometimes i think the cable company sometimes has issues. cause if it works everywhere else and such then it is definitely prob not the laptop itself. does your router use wpa password or is it open connection, have you reset the router? are you absolutely sure the password is correct and with the right capital and lowercase letters as original? mine is not a passphrase it is numbers and letters and I have accidentally hit another key when it popped up before cause it disconnected for some reason and put that extra letter in there that i was sure was not there i thought and later redid it and it worked. so prob your cable/dsl company (maybe call them have them reset it on their side also) or it is router itself. since the laptop works fine elsewhere i would just reset router and if not working call the company.

---

### Post by Wuxin on 2012-12-17
Thanks for the reply.  No, this has been going on now for about three days.  I too thought it might be just a temporary glitch, but it isn't.  The problem seems to be with the authentication process when I first log on.  If I right click on the wireless icon at the top of the screen, I can see my router id as well as the router id's of my neighbors.  When the authentication box appears on the screen, sometimes it has my router id and sometimes it has my neighbors' id's.  When I insert my password, the little logo in the upper right hand corner of the screen keeps rotating and rotating, but it never connects to the internet.  I tried calling my dsl company today and they walked me through the process and assured me that everything is functioning as it should be from that end.  I'm at a loss to know how to repair this.  My hunch is it's probably something simple but I just can't figure out what it is.  Anyone have any ideas?

---

### Post by slixz85 on 2012-12-18
are you using wpa? i assume most likely you are if that is the case then assure yourself that wpa supplicant is installed. i believe this is all that is needed for wpa   sudo apt-get install wpasupplicant  and if it is installed try reinstalling and rebooting then try again. let me know

if not let me know wep or what

---

### Post by slixz85 on 2012-12-18
also try to use wicd instead and after install click preferences and put in what your wifi connection is into preferences (wlan0 or wlan1 (whatever ifconfig or iwconfig pulls back) cause by default it usually dont find it. network-manager works fine for me but some people get problems

---

### Post by Wuxin on 2012-12-18
Wait...you're losing me a bit here!  I'm not an expert in the ways of Linux yet!  Yes, I believe I have WPA--actually it's wpa/wpa2.  But how do  you reinstall that?  It's been so long since I set that stuff up that I've forgotten how to do it.  I don't know  what wicd is...instead of what?  And click "preferences" under what?  I'm not exactly sure what you're referring to here.  If all this is to be done in the router set up window, I have to do that on my desktop because I don't have access to it through my Xubuntu laptop.  Thanks for your help, I just need a bit more explanation so that I know how to execute these things.  Thanks again!

---

### Post by slixz85 on 2012-12-18
sure no problem man. there are two ways. one is called synaptic which is more friendly to new users. just open up synaptic the package manager and under the search type in "wpasupplicant" (without quotes of course). it will pull back 1 result then if the box is filled then it is installed and if it is then left click it and hit reinstallation and if it is not then just click install. also after you do that type in the search box "wicd" and click install. now after you did this it is not installed already you have to click apply which is an arrow near the search box then click yes or apply again and it will download and then install the packages. it will take a few minutes depending on your internet speed.

now after this is all installed or reinstalled then click your start menu and find the application called terminal which pops up a black box with your computer hostname and your username then type in it "ifconfig" or "iwconfig" it will pull a couple results hopefully. look for wlan0 or wlan1. now whatever this shows match it in wicd. open up wicd from the program start menu and then click the arrow for preferences might have to resize the window to see preferences. then once in preferences under wireless connection the box MAY be empty. type in wlan0 or wlan1 whatever it pulled back from ifconfig or iwconfig. then apply and hit refresh once it shows networks then click connect and it will ask your for your password.
there should be no need to restart your computer at all but it don't hurt. Let me know whats up after this.




i am runnin a little late to work. i get caught up sometimes lol. i only gotta run in and out though to fix somethin. i be back later but go ahead and try this out and i will read when i get back

---

### Post by kurt18947 on 2012-12-18
Another option would be to *temporarily* disable wireless security.  You'd have to do this at your router or access point.  If you disable security and are then able to connect,  there may a problem with with the nm-applet.  If you disable security in the wireless section of your router and still can't connect, then something else is causing grief.

---

