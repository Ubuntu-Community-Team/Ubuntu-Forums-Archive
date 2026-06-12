---
title: "Screen freezes. Only option is to press the power button"
date: 2013-11-03
forum: General Help
---

### Post by J_Me on 2013-11-03
What could be causing my laptops screen to freeze with blue coloring    [http://postimg.org/image/dcvug6wxd/](http://postimg.org/image/dcvug6wxd/)  I had to make this image in gimp(a photo was no good) it's close to what I see on the screen but the blue flickers. The only option I have is to press the power button to restart the computer. This happens randomly. I've taken apart the laptop to checks for loose bits. It's a dell inspiron mini 1010 and I'm using kubuntu 12.04  TIA P.S. for some reason I unable to make a new line when writing this so everything is clumped together.

---

### Post by jamesisin on 2013-11-03
One thing you might try in order to get more evidence gathered is *ssh* into your machine and run *top* to see what you see.  If you haven't already done this, you need to install an ssh server on your machine:

```
sudo apt-get install openssh-server
```

Once that is installed you can *ssh* into your machine to test things using this format:

```
ssh username@machinename
```

Running *top* is merely thus:

```
top
```

(Pressing *q* will quit *top*.)

---

### Post by J_Me on 2013-11-04
@jamesisin thanks for the reply

---

### Post by jamesisin on 2013-11-04
Hope it helps.

---

### Post by mikewhatever on 2013-11-30
Actually, Dell's Inspiron 1010 is kind of infamouse for freezes. I have one that does the same. There is no blue, which is probably irrelevant, the machine just stops responding with no clues in the logs. I've tried ssh some years back with ... probably 9.10, and it failed to connect, I can also attest that it did it with all versions of Ubuntu from 9.04 through 12.04. I've even gone so far as upgrading the BIOS to the latest version, all to no avail. The problem is, apparently, not Limited to Ubuntu, but has been reported to happen with Windows XP.
[http://en.community.dell.com/support-forums/software-os/f/3524/t/19409569.aspx](http://en.community.dell.com/support-forums/software-os/f/3524/t/19409569.aspx)
[http://en.community.dell.com/support-forums/software-os/f/3525/t/19300868.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19300868.aspx)
[http://www.freesoftwaremagazine.com/articles/open_letter_michael_dell_why_i_have_no_choice_return_my_ubuntu_inspiron_mini_10](http://www.freesoftwaremagazine.com/articles/open_letter_michael_dell_why_i_have_no_choice_return_my_ubuntu_inspiron_mini_10)

I don't know what causes it, but the best you can do is relax, reboot, and go on with what you were doing.

---

