---
title: "How to get Logitech Cordless Bluetooth Mouse+Keyboard set working in ubuntu?"
date: 2007-02-27
forum: General Help
---

### Post by Iced_Kirby on 2007-02-27
First of all, I'm an absolute beginner.

Anyway, my default keyboard+mouse is [this.]("http://www.logitech.com/index.cfm/products/details/CA/EN,CRID=2158,CONTENTID=10776") 
It runs on bluetooth. On my first ubuntu run, I found out that bluetooth doesn't seem to work just like that, so I resorted to a wired set.

So, does anybody know how to get bluetooth working on ubuntu?

Thanks,

-Iced_Kirby

---

### Post by Iced_Kirby on 2007-02-27
Is there a user-friendly tutorial anywhere? That would be nice :KS

---

### Post by Iced_Kirby on 2007-02-28
Anybody?

---

### Post by nerdman978 on 2007-02-28
Mhm. I think I might be able to help you in your plight. 

Open the GNOME terminal. 
type in 'hcitool scan' (without the apostrophes)
The bluetooth keyboard and mouse should be in the results (make sure they're plugged in)
Next, you will see MAC addresses next to the results (series of numbers)
write these numbers down

Then, open up the terminal again type 
'sudo hidd --connect xx:xx:xx:xx:xx:xx' 
where x is the MAC address 

once you've done this for the keyboard and mouse (i looked at the images, those are NICE)
Ubuntu will work with these devices!!!

good luck

---

### Post by nerdman978 on 2007-02-28
Hmm it appears the above message didn't let me put x's in a row :) 

Just insert the MAC address and you'll be ok.

---

### Post by Iced_Kirby on 2007-03-01
> **nerdman978 said:**
> Mhm. I think I might be able to help you in your plight. 

Open the GNOME terminal. 
type in 'hcitool scan' (without the apostrophes)
The bluetooth keyboard and mouse should be in the results (make sure they're plugged in)
Next, you will see MAC addresses next to the results (series of numbers)
write these numbers down

Then, open up the terminal again type 
'sudo hidd --connect xx:xx:xx:xx:xx:xx' 
where x is the MAC address 

once you've done this for the keyboard and mouse (i looked at the images, those are NICE)
Ubuntu will work with these devices!!!

good luck

It doesn't find anything.

---

### Post by Iced_Kirby on 2007-03-01
Making progress! 1/2 done! :) 

Using [this]("https://help.ubuntu.com/community/BluetoothMouse?highlight=%28CategoryBluetooth%29") I got the keyboard working. Problem is, it doesn't find the mouse!

The doc says to use the address if it doesn't work. I have a problem here, the paper on the bottom of the mouse that says the address is all scratched! 

Can somebody help me find a picture on the net of the bottom of my mouse? (Click link in first post)

---

### Post by Iced_Kirby on 2007-03-01
Thread Closed!

I got both connected!

( I had to hold down the connect button on the mouse ;) )

---

### Post by Iced_Kirby on 2007-03-01
THREAD OPENED AGAIN.
I have a dual-boot with Windows XP and Ubuntu.

Mouse is fine between the two. But the keyboard is not.

After connecting the keyboard in ubuntu. I went to XP. The keyboard wasn't working and wouldn't connect.

---

### Post by Iced_Kirby on 2007-03-01
Any reported cases of this?

---

### Post by Iced_Kirby on 2007-03-04
'Alo?

---

### Post by dnns on 2007-03-29
Have you tried out the info in this thread:

[http://ubuntuforums.org/showthread.php?t=227057&page=2&highlight=dinovo](http://ubuntuforums.org/showthread.php?t=227057&page=2&highlight=dinovo)

?

---

