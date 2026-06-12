---
title: "Line 4: Word Unexpected, Expecting &quot;do&quot;"
date: 2008-03-02
forum: General Help
---

### Post by bobmart32 on 2008-03-02
I'm using a code here to create a node for my USB CDU Franklin Wireless modem(From Alltel). Unfortunately, it won't work. Problem? I run the program as a .sh file and terminal says "line 4, word unexpected. expecting "do". Yet, I look on line 4 and there is clearly a "do" there. what do I do? =(

#!/bin/bash
# usb : acm
echo -e "\033[32mMake Modem Device\033[0m"
for i in `seq 0 2` ; do
mknod /dev/ttyACM$i c 166 $i
done

echo -e "\033[32mMake Dual Mode Device\033[0m"
for i in `seq 0 2` ; do
mknod /dev/ttyUSB$i c 188 $i
done

echo -e "\033[32mMake driver rule\033[0m"
/sbin/modprobe usbserial vendor=0x16d8 product=0x5511
/sbin/modprobe usbserial vendor=0x16d8 product=0x5512
/sbin/modprobe usbserial vendor=0x16d8 product=0x5513
/sbin/modprobe usbserial vendor=0x16d8 product=0x5521
/sbin/modprobe usbserial vendor=0x16d8 product=0x5522
/sbin/modprobe usbserial vendor=0x16d8 product=0x5523
/sbin/modprobe usbserial vendor=0x16d8 product=0x5531
/sbin/modprobe usbserial vendor=0x16d8 product=0x5532
/sbin/modprobe usbserial vendor=0x16d8 product=0x5533
/sbin/modprobe usbserial vendor=0x16d8 product=0x5541
/sbin/modprobe usbserial vendor=0x16d8 product=0x5542
/sbin/modprobe usbserial vendor=0x16d8 product=0x5543
/sbin/modprobe usbserial vendor=0x16d8 product=0x5551
/sbin/modprobe usbserial vendor=0x16d8 product=0x5552
/sbin/modprobe usbserial vendor=0x16d8 product=0x5553
/sbin/modprobe usbserial vendor=0x16d8 product=0x5561
/sbin/modprobe usbserial vendor=0x16d8 product=0x5562
/sbin/modprobe usbserial vendor=0x16d8 product=0x5563
/sbin/modprobe usbserial vendor=0x16d8 product=0x6011
/sbin/modprobe usbserial vendor=0x16d8 product=0x6012
/sbin/modprobe usbserial vendor=0x16d8 product=0x6013
/sbin/modprobe usbserial vendor=0x16d8 product=0x6021
/sbin/modprobe usbserial vendor=0x16d8 product=0x6022
/sbin/modprobe usbserial vendor=0x16d8 product=0x6023
/sbin/modprobe usbserial vendor=0x16d8 product=0x6511
/sbin/modprobe usbserial vendor=0x16d8 product=0x6512
/sbin/modprobe usbserial vendor=0x16d8 product=0x6513
/sbin/modprobe usbserial vendor=0x16d8 product=0x6521
/sbin/modprobe usbserial vendor=0x16d8 product=0x6522
/sbin/modprobe usbserial vendor=0x16d8 product=0x6523
/sbin/modprobe usbserial vendor=0x16d8 product=0x6531
/sbin/modprobe usbserial vendor=0x16d8 product=0x6532
/sbin/modprobe usbserial vendor=0x16d8 product=0x6533
/sbin/modprobe usbserial vendor=0x16d8 product=0x6541
/sbin/modprobe usbserial vendor=0x16d8 product=0x6542
/sbin/modprobe usbserial vendor=0x16d8 product=0x6543
/sbin/modprobe usbserial vendor=0x16d8 product=0x6551
/sbin/modprobe usbserial vendor=0x16d8 product=0x6552
/sbin/modprobe usbserial vendor=0x16d8 product=0x6553
/sbin/modprobe usbserial vendor=0x16d8 product=0x6561
/sbin/modprobe usbserial vendor=0x16d8 product=0x6562
/sbin/modprobe usbserial vendor=0x16d8 product=0x6563

---

### Post by mrpixels0 on 2008-03-02
did you do do it as root ?, sometimes these things have to be done as root to work properly. wierd I know but it has happened to me before.

MP0

---

### Post by bobmart32 on 2008-03-02
I use Sudo, isn't that the same thing?

---

### Post by bobmart32 on 2008-03-03
Bump.

Well? Whats wrong with this .sh file? Why can't it detect "do" on line 4?

---

### Post by bobmart32 on 2008-03-03
The code I'm using for the .sh file can be found in the OP here: [http://ubuntuforums.org/showthread.php?t=713546](http://ubuntuforums.org/showthread.php?t=713546)
Hasn't been answered yet. I require this .sh file to get my internet on linux to run. Tell me, why is it saying its expecting "do" when it is clearly there?

---

### Post by ellgor on 2008-03-03
Hi,

Had a quick look at the readout and from what I can see that do is not on line 4, explanation, the first two lines of that code have a #which means ignore, so counting from after them the do appears on line 2, hope this makes sense and hope it helps.

Regards, Ellgor.

---

### Post by bobmart32 on 2008-03-03
No, sorry. The Synatx error keeps hapanning =( I may not be adding it right though. How would I add "do" in line 4 so that the terminal will recognize it? I keep putting "do" after the word Done and " ; do" and,s everal other things. I'm stumped on this one. I THINK I've added to the code but, it still not recognized. woe me =(

---

### Post by Lord Illidan on 2008-03-03
Try running it like this :

/bin/bash <name>.sh

---

### Post by bobmart32 on 2008-03-03
Bumb. I WILL get internet on my linux.

---

### Post by bodhi.zazen on 2008-03-03
Try getting rid of the spaces:

> for i in `seq 0 2`;do

Also, please do not create multiple threads re: same issue.

---

### Post by bobmart32 on 2008-03-03
^-----Well, that fix one problem but now, I've got another problem:
This is now the error I get after ollowing Bodhi's advice:
> Name@Name:~$ sudo chmod a+x Filename.sh
[sudo] password for Name:
Name@Name:~$ sudo sh ./Filename.sh
: not foundsh: 3: 
-e Make Modem Device
./Filename.sh: 5: Syntax error: word unexpected (expecting "do")
Name@Name:~$ 
help =(.

---

### Post by bodhi.zazen on 2008-03-03
You seem to have a number of syntax errors in your script. Where did you get it ?

You can comment out the third line (the one with the echo command) by adding a # at the front (you really do not need that echo statement).

You need to go through the script an remove other spaces around the ; and do

You probably need to quote i or possibly add brackets { }

mknod /dev/ttyACM"${i}" c 166 "$i"

---

### Post by ghostdog74 on 2008-03-03
try
```

sudo bash ./Filename.sh

```
or 
```

sudo ./Filename.sh

```

---

### Post by bobmart32 on 2008-03-04
Ok, this is the complete code I'm now using, I changed it a little: (Thanks to Bodhi)

> 
#!/bin/bash
# usb : acm

#echo -e "\033[32mMake Modem Device\033[0m"
for i in `seq 0 2`;do
mknod /dev/ttyACM${i} c 166 ${i}
done

echo -e "\033[32mMake Dual Mode Device\033[0m"
for i in `seq 0 2`;do
mknod /dev/ttyUSB${i} c 188 ${i}
done

echo -e "\033[32mMake driver rule\033[0m"
/sbin/modprobe usbserial vendor=0x16d8 product=0x5511
/sbin/modprobe usbserial vendor=0x16d8 product=0x5512
/sbin/modprobe usbserial vendor=0x16d8 product=0x5513
/sbin/modprobe usbserial vendor=0x16d8 product=0x5521
/sbin/modprobe usbserial vendor=0x16d8 product=0x5522
/sbin/modprobe usbserial vendor=0x16d8 product=0x5523
/sbin/modprobe usbserial vendor=0x16d8 product=0x5531
/sbin/modprobe usbserial vendor=0x16d8 product=0x5532
/sbin/modprobe usbserial vendor=0x16d8 product=0x5533
/sbin/modprobe usbserial vendor=0x16d8 product=0x5541
/sbin/modprobe usbserial vendor=0x16d8 product=0x5542
/sbin/modprobe usbserial vendor=0x16d8 product=0x5543
/sbin/modprobe usbserial vendor=0x16d8 product=0x5551
/sbin/modprobe usbserial vendor=0x16d8 product=0x5552
/sbin/modprobe usbserial vendor=0x16d8 product=0x5553
/sbin/modprobe usbserial vendor=0x16d8 product=0x5561
/sbin/modprobe usbserial vendor=0x16d8 product=0x5562
/sbin/modprobe usbserial vendor=0x16d8 product=0x5563
/sbin/modprobe usbserial vendor=0x16d8 product=0x6011
/sbin/modprobe usbserial vendor=0x16d8 product=0x6012
/sbin/modprobe usbserial vendor=0x16d8 product=0x6013
/sbin/modprobe usbserial vendor=0x16d8 product=0x6021
/sbin/modprobe usbserial vendor=0x16d8 product=0x6022
/sbin/modprobe usbserial vendor=0x16d8 product=0x6023
/sbin/modprobe usbserial vendor=0x16d8 product=0x6511
/sbin/modprobe usbserial vendor=0x16d8 product=0x6512
/sbin/modprobe usbserial vendor=0x16d8 product=0x6513
/sbin/modprobe usbserial vendor=0x16d8 product=0x6521
/sbin/modprobe usbserial vendor=0x16d8 product=0x6522
/sbin/modprobe usbserial vendor=0x16d8 product=0x6523
/sbin/modprobe usbserial vendor=0x16d8 product=0x6531
/sbin/modprobe usbserial vendor=0x16d8 product=0x6532
/sbin/modprobe usbserial vendor=0x16d8 product=0x6533
/sbin/modprobe usbserial vendor=0x16d8 product=0x6541
/sbin/modprobe usbserial vendor=0x16d8 product=0x6542
/sbin/modprobe usbserial vendor=0x16d8 product=0x6543
/sbin/modprobe usbserial vendor=0x16d8 product=0x6551
/sbin/modprobe usbserial vendor=0x16d8 product=0x6552
/sbin/modprobe usbserial vendor=0x16d8 product=0x6553
/sbin/modprobe usbserial vendor=0x16d8 product=0x6561
/sbin/modprobe usbserial vendor=0x16d8 product=0x6562
/sbin/modprobe usbserial vendor=0x16d8 product=0x6563


An this is what I'm getting:
> Name@Name:~$ sudo bash ./Filename.sh
: command not found 3: 
'/Filename.sh: line 5: syntax error near unexpected token `do
'/Filename.sh: line 5: `for i in `seq 0 2`;do


---

### Post by bodhi.zazen on 2008-03-05
I have no idea why you get that error message, 

> for i in `seq 0 2`;do
# mknod /dev/ttyACM${i} c 166 ${i}
echo $i
done
runs just fine, and output =

0
1
2

So you can shorten your script with :

```
for i in {0,1,2};do
mknod /dev/ttyACM${i} c 166 ${i}
mknod /dev/ttyUSB${i} c 188 ${i}
done
```

script otherwise runs here ???

---

### Post by yellowbread on 2008-03-05
Which modem do you have? As far as I know, Franklin models of usb evdo modems include CDU-550. CDU-650, CDU-680, CCU-550, and CHU-628. The script you are trying to run supposedly works for the CDU-550. I don't know anything about the CDU-650, CCU-550, or CHU-628, but the CDU-680 requires a different approach.

---

### Post by bobmart32 on 2008-03-05
It says: EVDO usb modem, on the side it says: CDU-550. Yea, it is.

---

### Post by yellowbread on 2008-03-05
With the 550, I only know what I have read about it. Is that script running yet? You can leave out most of the modprobe statements if you know the product id for your modem. What does 

```
lsusb
```

in a terminal give as output?

---

