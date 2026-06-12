---
title: "Heping instaling drivers on an old computer"
date: 2019-09-27
forum: General Help
---

### Post by miguelrbls on 2019-09-27
Hello, 

This is my first post, I'm new on Linux.

I've found an old PC which is working, it's an AsRock775i65GG with a ViewSonic Monitor VA703b and I installed Lubuntu on it but the problem is after the installation seems like the drivers are nor installed because I cannot select the correct resolution (1280 x 1024) and I have that horrible vertical black line on right side of the monitor.

I've tried creating a xorg.conf file in order to add the correct resolution and "it works". I keep having the same problem with the black line and all looks horrible. Here is a picture:

[ATTACH=CONFIG]284094[/ATTACH]

So I think a need to manually install the drivers and make sure the system is using them. The problems are: I don't know what drivers do I have to install, how do I install them and how do I make sure the system is using them?

Do not be afraid to explain me the things like a child. I'm new and I'm willing to learn.

Thanks!

---

### Post by slickymaster on 2019-09-27
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by uRock on 2019-09-27
Hello and welcome.

I've found that some monitors have a button to adjust the incoming image to fit the screen, which resolves the black line down the side.

For drivers, you should be able to open Software Sources, then click the Additional Drivers tab, then select a graphics driver.

---

### Post by miguelrbls on 2019-09-27
> **uRock said:**
> Hello and welcome.

I've found that some monitors have a button to adjust the incoming image to fit the screen, which resolves the black line down the side.

For drivers, you should be able to open Software Sources, then click the Additional Drivers tab, then select a graphics driver.

Hi,

I've tried adjusting the image with the buttons located on the monitor and doesn't work. 

And there's nothing on the addiotional drivers section. It's greyed out.

---

### Post by miguelrbls on 2019-09-27
> **slickymaster said:**
> Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

Oh, sorry.

---

### Post by deadflowr on 2019-09-27
We'd need to see
```
xrandr -q
lspci | grep VGA
```
for starters.

---

### Post by MoebusNet on 2019-09-27
Just to let you know a couple of things; **first** both the PC and the monitor are quite old (for a computer) - they both look to be about 2003 vintage. I'm even kind of surprised that Lubuntu supports them at all; the PC uses the outdated AGP video bus and the monitor uses an old VGA cable to connect - nothing high definition there. **Second**, the issue isn't a "driver" as you suppose. The issue is that the current driver doesn't recognize the proper resolution the monitor needs. To fix this, you will need to manually insert the proper resolution into the file that holds the supported resolution. You do this by using the application LXTerminal (Menu>System Tools>LXTerminal), finding the proper file, and typing the needed resolution into the file. Here is an example to do that from a couple of years ago: [http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/) If you are familiar with Windows, this is kind of like using DOS to modify configuration files.

Honestly, it might be easier all around to try a different Operating System designed specifically for older computers. The one I've had the best success with is called 'antiX'. Here is the website about it: [https://antixlinux.com/](https://antixlinux.com/). This is a Debian-based OS (like Ubuntu is) optimized for older PC's. it should have most of the bugs you are dealing with worked out already. If that is not to your taste, Distrowatch.com lists a number of OS's specifically for older computers. Best of luck!

---

### Post by MoebusNet on 2019-09-27
@deadflwr - I'm not trying to step on your toes; you posted before I could finish typing. Best of luck!

---

### Post by Autodave on 2019-09-27
+1 with uRock: that appears to be an issue with the monitor not centering the image.  Check your buttons again.  There is a slight possibility that it could also be your VGA cable: try another known-good one.  Lastly, you could have a failed/failing monitor.

---

### Post by Autodave on 2019-09-27
When you first enter the onscreen menu, AUTO ADJUST should be the top choice.  Choosing that should get you aligned.  If not, going down the menu is the MANUAL ADJUST wher you can do the same thing manually.

---

### Post by miguelrbls on 2019-09-27
> **deadflowr said:**
> We'd need to see
```
xrandr -q
lspci | grep VGA
```
for starters.

Of course, the result from xrandr -q:

Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
VGA1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x1024     59.89 +
   1280x1024_60.00  59.89* 
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

When I put "grep VGA" it does nothing...

---

### Post by mörgæs on 2019-09-29
You could also try ```
lshw -C video
```
Please post the result in CODE tags.

---

### Post by guiverc on 2019-09-29
I wondering what release of Lubuntu you installed on your machine.  

Have you update software lists (`sudo apt update`) which I'm asking because of the greyed-out drivers; but without your release I'm guessing (my Lubuntu reports 'no drivers found' when none are found). I booted up a pentium 4 box with Lubuntu 18.04 LTS and in the 'Software & Updates' tab I get "No additional drivers available", but I'd like confirmation of release.

(fyi:  there are many sites that offer Lubuntu as well as other Linux distros that are not official.  Lubuntu has many 'fan' sites that offer downloads that may or may not be the same as the official ISO.  I suggest ensuring you get an official ISO by going to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) to grab a Ubuntu flavor, and not searching google; which I suspect favors sites with its advertizing (there is no advertizing on the official sites).  The official site is [http://lubuntu.me]("http://lubuntu.me/") )

---

