---
title: "using zipped files"
date: 2013-02-23
forum: General Help
---

### Post by vegan1 on 2013-02-23
I tried to download a piece of aircraft for a flight simulator as a zipped file. It would dl onto the desktop. Then, I would unzip it and I couldn't move it into the file where it needs to go for the game.

Then, I tried to dl the file into the correct folder and I pressed the save button and nothing happened. What is going on? What is file roller and why am I using Archive Manager? I tried to use the GUI for this task and I would rather use the GUI than try to make sure I type in every file correctly. Also, the mv command confuses me with figuring out how to specify both files, the one where the file is and the one where you want it to go.

---

### Post by matt_symes on 2013-02-23
Hi

Where are you trying to install it to ? It sounds like you have a permission issue.

Open nautilus with elevated privileges and try to move the fil.

```
gksudo nautilus
```

Kind regards

---

### Post by ali abry on 2013-02-23
why couldn't you move it to destination you want ? did you get any error ?

here is how to use mv command :
```
 mv SOURCE-FILE     DESTINATION-FILE
```
note that in above command : if the destination file doesn't exist your file will be rename to DESTINATION-FILE

---

### Post by 2F4U on 2013-02-23
Maybe you are downloading into a folder where your normal user has no privileges?

---

### Post by vegan1 on 2013-02-23
I think you are all right about the user privileges. Thanks for helping so fast! It is an amazing resource and so friendly and not condescending if you are a beginner!

Okay, I opened up Nautilus with the gksudo command and put the unzipped file on the desktop, but when I clicked on desktop, the whole thing was blank. Yes, I tried it, again. When I open up Nautilus normally, I can see the folder in the desktop.

---

### Post by howefield on 2013-02-23
> **vegan1 said:**
> I tried to download a piece of aircraft for a flight simulator as a zipped file.

What's the name of the extracted file and where do you want it to go ?

---

### Post by vegan1 on 2013-02-23
The file is 'Alphajet'
The destination folder is 'usr, share, games, FlightGear, Aircraft

---

### Post by matt_symes on 2013-02-23
Hi

It may be easier to use the terminal

```
sudo mv ~/Desktop/Alphajet /usr/share/games/FlightGear/Aircraft
```Kind regards

---

### Post by jmore9 on 2013-02-23
Did you try just putting sudo in front of the mv command ?  Sometines I have to do that like with my tv tuner card drivers and moving them.

---

### Post by vegan1 on 2013-02-23
Wow, thanks Matt. It's magic! It worked.

---

