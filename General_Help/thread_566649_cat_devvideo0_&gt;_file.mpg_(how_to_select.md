---
title: "cat /dev/video0 &gt; file.mpg (how to select"
date: 2007-10-03
forum: General Help
---

### Post by bone2006 on 2007-10-03
I'm running mythtv with one tuner card with two inputs.  I have one setup as Tuner 1 on /dev/video0 and another setup as Composite 1 on  /dev/video0 .

I'm able to switch just fine in mytthtv between my cable and my satelite.  The problem is I'd like to record from the command line.  When I type in cat /dev/video0 > file.mpg

it records from the tuner/coax and not from the composite.  What command do I need to type so that I can tell it to record from satellite the way it's working in mythtv?

Thanks in advance

---

### Post by rsambuca on 2007-10-03
The command will differ depending on your tuner card.  Tough to help you without info!

---

### Post by bone2006 on 2007-10-03
ivtv is the driver that was loaded by default and the card is Hauppauge PVR-150 PCI Interface Tuner Card
sorry for not putting more info earlier

---

### Post by rsambuca on 2007-10-04
Same card as mine.  This will set the input to composite.

v4l2-ctl -d /dev/video0 --set-input=2

---

### Post by bone2006 on 2007-10-04
thank you so much
just to make sure if I wanted to just fire up the terminal and record really quick could I type this in:


v4l2-ctl -d /dev/video0 --set-input=2 > /home/user/record/file.mpg 

just one last question, is there anyway to use a command so that it's not always called file.mpg?  What I mean is that I'd like to just fire up the terminal run this command and have it save in the directory /home/user/record/ but what if I already have a file.mpg, wouldn't it over write the current file?

Thanks again

---

### Post by newlinux on 2007-10-04
You can name the file whatever you want:
```

cat /dev/video0 >/home/user/record/PushingDaisies.mpg

```
for example.

Also, I think what you would do is type:
```

v4l2-ctl -d /dev/video0 --set-input=2

```
then type
```

cat /dev/video > /home/user/record/BionicWomanFromSatellite.mpg

```
to record from satellite. Someone correct me if I'm wrong.

---

### Post by bone2006 on 2007-10-04
well I'm aware you can name the file what ever you want, but I was going to make an alias of


alias recordsat='cat /dev/video > /home/user/record/BionicWomanFromSatellite.mpg'

therefore the file would always be the same.  I really don't want to type out that every time for obvious reasons.  I'd like to just type in recordsat and press enter and go about my business.  So you can see why I'd like to have the ability to not have to look into the directory to see if there's already the file with the same name already there.

---

### Post by newlinux on 2007-10-04
I think trying to do that with an alias would be problematic. Write a short bash script that takes as an argument the filename would probably be better, or/and you could have it check for the file and if it exists write a different filename. Another good reason to make it a script because you are going to have to run two commands, one to change the input and one to record from the input.

---

