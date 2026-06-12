---
title: "Tutorial: Extend laptop battery life."
date: 2013-03-16
forum: General Help
---

### Post by sam_uk on 2013-03-16
I'm no expert in any of this. I just spent a couple of boring hours Googling this afternoon and thought I would share what I found. I am living on a off-grid 12v system so power conservation is pretty important to me.  I don't have one of those handy watt meters. Therefore this whole tutorial is based on the assumption that the Jupiter and Powertop developers know what they are doing. However I have seen a drop in CPU temp since making these changes so that is a encouraging sign. Your milage may vary. It would be great if anyone who has a watt meter could test this and post results below.

[B][SIZE=3]==Screen Backlight==[/SIZE]
[/B]
**Turn it down** as low as your eyes are happy with. Simples.


**[SIZE=3]==Desktop Managers==[/SIZE]**

According to this: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_precise_desktop&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_precise_desktop&num=1)

The Unity desktop is one of the worst for power consumption.

According to this: [http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce) the minimum CPU needed for Unity=1Ghz, Gnome-shell=400 MHz, LXDE=  266 MHz

So if you really want to save power then: 

```
sudo aptitude install lxde-core 

```
**Log out then back in to LXDE**. There are even lighter weight ones, openbox for example but that's probably too minimal for most peoples tastes.

Personally I am more productive in gnome-shell so for my daily driver I use this: 

```
sudo aptitude install gnome-shell 

```
You can install both on your machine and swap between them. If it's a cloudy day, or I am on a long train ride I will use LXDE. This should save you a couple of watts.


[B][SIZE=3]==Jupiter==[/SIZE]
[/B]
Is a program that helps you to manage your power. Ref: [http://www.fewt.com/2010/02/meet-jupiter.html](http://www.fewt.com/2010/02/meet-jupiter.html) Mostly it works automatically, but there is an option to set manually. This is useful for me as I live on 12v off grid power. I want to tell my laptop to conserve power even when it thinks it is connected to mains. More: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

```
sudo add-apt-repository ppa:webupd8team/jupiter

``````
sudo aptitude update
```
```
sudo aptitude install jupiter
```

If you have already switched to the gnome-shell desktop the icon is in the bottom right corner once you hover the mouse in the top-left corner. If you are still in Unity or using LXDE it shows up in the system tray as a lightning bolt icon. 


[B][SIZE=3]==Powertop==[/SIZE]
[/B]
This is a comand line app and it's bit fiddly to get the settings to stick.

```
sudo aptitude install powertop

```
```
sudo powertop --html

```
```
sudo chmod 666 PowerTOP.html

```
```
firefox PowerTop.html

```

When firefox opens with your report **click 'tuning' tab on top righ**t.

Warning: Ensure that only the commands are transferred from the PowerTOP HTML file (right column), and not their preceding explanations (left column). 

To do this I found it easiest to; **Open a new Libre office spreadsheet, Copy and paste the info from Firefox to spreadsheet, Delete the irrelevant (left hand) column **

Back in the terminal:

```
sudo gedit /usr/local/bin/startup.sh
```

**Copy text from your spreadsheet to the gedit file. Save. Close.**

```
sudo chmod +x /usr/local/bin/startup.sh
```

```
sudo gedit /etc/rc.local
```


**Remove the # symbol at the beginning of the first line ** so it reads:

```
!/bin/sh -e
```

**Add this to the Gedit file above where it says 'Exit 0':** 

```

/usr/local/bin/startup.sh
rfkill block bluetooth

```

(This will also off bluetooth by default)


[B]Save & close
[/B]

**Reboot your machine**

If you like you can run powertop again to make sure it worked.

Mostly nicked & slightly simplified from:[http://wiki.manjaro.org/index.php/PowerTOP_to_Optimise_Laptop_Power_Consumption](http://wiki.manjaro.org/index.php/PowerTOP_to_Optimise_Laptop_Power_Consumption)

[B]==Samsung Specific==
[/B]
I was having problems getting Bluetooth to be off by default. I happened to be looking through 'boot up manager' and noticed 'Samsung tools' I enabled this to start on boot and now can access a little app that allows you to turn off Bluetooth by default for Samsungs.

```
sudo aptitude install samsung-tools bum
```

Update: I just had a look at the 'power statistics' app in my Samsung N220

With Wifi off, powersave mode, backlight dim it says I am consuming 8.2 watts

With Wifi on, powersave mode, backlight dim it says I am consuming 8.8 watts

With Wifi on, full power mode, backlight dim it says I am consuming 12.2 watts

In LXDE desktop:

Backlight full, Wifi off, powersave mode: 7.8 watts

Backlight full, Wifi on, powersave mode: 11.4 watts

In Openbox desktop:

Backlight full, Wifi off, powersave mode: 7.8 watts so no real gain over LXDE

Estimated battery life is around 7 hours which seems pretty good to me.

Be great if anyone could report back on their experiences of the above tweaks + watt meter.


Thanks

Sam

---

