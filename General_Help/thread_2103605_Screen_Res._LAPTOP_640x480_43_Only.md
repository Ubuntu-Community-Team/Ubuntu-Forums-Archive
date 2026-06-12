---
title: "Screen Res. LAPTOP 640x480 4:3 Only?"
date: 2013-01-10
forum: General Help
---

### Post by Rachambers on 2013-01-10
I am a semi-new user to Ubuntu. I usually have no problems. This time i downloaded the newest version of Ubuntu and am STUCK with my display resolution saying [COLOR=Red]Laptop 640x480 4:3 [/COLOR]...but im not using a laptop

The screen WONT let me change it and when I try to the screen is too BIG for the resolution setting. Clicking and dragging wont let me see the bottom of the screen only side to side.... trying to shape it smaller isnt working because its already as small as it can get. 

I would prefer it to be 1280x1024 but i am not sure How.

below is what i See.
[IMG]http://i1305.photobucket.com/albums/s550/rachambers55/Screenshotfrom2013-01-10161220_zpse9781670.png[/IMG]

---

### Post by Muratturat on 2013-01-10
> **Rachambers said:**
> I am a semi-new user to Ubuntu. I usually have no problems. This time i downloaded the newest version of Ubuntu and am STUCK with my display resolution saying [COLOR=Red]Laptop 640x480 4:3 [/COLOR]...but im not using a laptop

The screen WONT let me change it and when I try to the screen is too BIG for the resolution setting. Clicking and dragging wont let me see the bottom of the screen only side to side.... trying to shape it smaller isnt working because its already as small as it can get. 

I would prefer it to be 1280x1024 but i am not sure How.

below is what i See.
[IMG]http://i1305.photobucket.com/albums/s550/rachambers55/Screenshotfrom2013-01-10161220_zpse9781670.png[/IMG]

Install Jupiter 
```
sudo add-apt-repository ppa:webupd8team/jupiter
```
```
sudo apt-get update
```
```
sudo apt-get install jupiter
```

---

### Post by Rachambers on 2013-01-10
i get 
> 
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer

when i tried to install
sudo add-apt-repository ppa:webupd8team/jupiter
------------------------------------------

when i tried
sudo apt-get install jupiter
i got this
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package jupiter

---

### Post by Rachambers on 2013-01-10
When i tried a second time the last code worked finally...

Still not working even tho i have jupiter now

---

### Post by Pjotr123 on 2013-01-10
What video card?

Create and post a hardware list in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)
(item 7)

---

### Post by Rachambers on 2013-01-10
I think i have a NVIDIA addidional drivers

but my graphics card is
GeForce FX 5500/AGP/SSE/3DNOW!

---

### Post by Pjotr123 on 2013-01-10
Please create and post a hardware list as I requested.

---

### Post by Rachambers on 2013-01-10
here is the hardware list

---

### Post by Pjotr123 on 2013-01-10
In view of your hardware characteristics I advise you to switch to Xubuntu 12.04: [https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

Xubuntu, because Ubuntu is definitely too heavy for your hardware.

Xubuntu 12.04 and not Xubuntu 12.10, as only Xubuntu 12.04 will provide the possibility to use the repaired nvidia-96 restricted driver. The repaired nvidia-96 is still in the Proposed repo, but will probably land in the normal repo's within a week. :)

---

### Post by Rachambers on 2013-01-10
thank you ALOT for your help. I will definitely think about switching over. the only reason i have ubuntu is because my family is all Ubuntu user.

---

