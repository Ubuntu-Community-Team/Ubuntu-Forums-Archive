---
title: "Fps capped at 60"
date: 2017-04-03
forum: General Help
---

### Post by erzis on 2017-04-03
Hello,
I have AMD Radeon 6870 GPU. Fps are capped at 60, because there is vsync setted to on by default on radeon driver. Well, that's what I've read. To turn it off I followed these steps:

1.Open terminal
2.sudo -i
3.gedit ~/.drirc
4.I pasted in:
<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
    <!-- Other devices ... -->
</driconf>

Nothing has really changed after that operation. Did I miss something? Any suggestions?
Oh, I found how to turn off vsync here: [https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off](https://wiki.archlinux.org/index.php/ATI#Turn_vsync_off)

Any kind of help will be appreciated. Thanks.

---

### Post by deadflowr on 2017-04-03
Try again and skip step #2.
The ~/.drirc file is in your own home folder and not root's.
Then see what happens.

---

### Post by erzis on 2017-04-03
Well, I skipped step 2. It did not work tho. Fps are still at 60. Should this file be empty? Should I restart my desktop after?

---

### Post by bengutengu on 2017-04-03
I had a similar issue and pretty much followed the exact process (making sure I saved the ~/.drirc file in my home folder) and it workked like a charm!

---

### Post by erzis on 2017-04-03
So do i just do
cd /
cd home 
cd erzis
gedit ~/.drirc
as a user(not root)?

---

### Post by deadflowr on 2017-04-03
> **erzis said:**
> So do i just do
cd /
cd home 
cd erzis
gedit ~/.drirc
as a user(not root)?
basically, yes.

~ = home folder for current user.
By default that would be whatever user you logged in as.
When you run sudo -i, you run as root and the ~ means inside root's own home folder (/root)
Normal login places you inside your user's home folder (/home/username)
So ~ is shorthand for /home/username.

By default the terminal should place you inside the user's home folder
the prompt should look something like
**bob@ubunutbob~$** that ~ symbol inside indicates that you are in the home folder for bob.
just as when you run sudo -i
it's show as
**root@ubuntubob~#** indicating that you are currently inside root's home folder.

hope that makes sense.

---

### Post by erzis on 2017-04-03
Thanks for your explanation. Appreciate that. When i did ^ it took me to the ~ as you said. Well, then I guess I'm doing everything right.
[https://gyazo.com/eea48d0b5391d3785e65639bb666ba54](https://gyazo.com/eea48d0b5391d3785e65639bb666ba54)

Still doesn't work tho ;c

---

