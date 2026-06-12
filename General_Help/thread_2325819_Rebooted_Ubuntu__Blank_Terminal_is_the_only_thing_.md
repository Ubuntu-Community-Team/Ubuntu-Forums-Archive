---
title: "Rebooted Ubuntu | Blank Terminal is the only thing showing"
date: 2016-05-25
forum: General Help
---

### Post by KloudAlpha on 2016-05-25
Idk what I did. I reinstalled the AMD drivers because it was acting weird. Upon restart, it boots up but there isn't any desktop environment or anything, Just a black screen with a terminal.

[IMG]https://lh3.googleusercontent.com/-r5vO70sz-8pvKi2csYLTxJB_h3RCmeQl3vK1Y4obkVilCDtRUnHp5GNEsfyh2AoIJt-U-Lb6UK2BgtH2N_379N_jBDaOJCKH5zYYTkes57_P-R5KzYOzFrZLWvQR8UA_paz47qK4o4MRnYszqdsu0h_WcLWx6dVLE22s-nlDHcfiVG538jepDNBk8hWjYajAXuR1deDe3Ai6LIcw-U__fHvyvPBvq3sPes5JODjZ8Cn_6wu64t6avK4b2_RjsboAsVF0NWcwtmYfmo5t4jEcL0G6soDrVMVscyAJQBFI0NVkAyuuABXdwjF0Z7MmGtGtwrRn3hKg6iG6XO53KPTdcjTegcOh8gCyrJ2BT4a1OtbiCMWoy7FDFR3jsitIOXuKHNsMCXe0T4dVfIiI9p7T3e0nmYt_JVX_B-jn0mtHC0LV4kaoeJO5oIcCT-qjFBtsYTtFO8M7HOeJwQsN5g44SCxcCsIWLmqMruQ6U4hzhQUCGfo-cvKXJfa44DL767j7jSk11iJnimF62JtlHtFQM3xzWCPu0uewo412H7aFHPS9hVSEt7Tml9SJNagx8sWRvvTx0gifsX1tvhDN5mPCp9gTpsU550=w898-h673-no[/IMG]

---

### Post by QIII on 2016-05-25
Hello!

What release of Ubuntu are you using, what graphics adapter does your machine have and which driver did you install?

---

### Post by KloudAlpha on 2016-05-25
> **QIII said:**
> Hello!

What release of Ubuntu are you using, what graphics adapter does your machine have and which driver did you install?
I'm using Xubuntu 16.04 LTS. My Graphics card is an AMD R9 280.

I performed this command to reinstall the driver, then I rebooted.

```

sudo apt-get --purge autoremove xserver-xorg-video-radeon && sudo apt-get install xserver-xorg-video-radeon

```

---

### Post by KloudAlpha on 2016-05-25
I did a thing, and now it shows this.

[IMG]https://lh3.googleusercontent.com/gZ0v1IXpK-T3Ei8xLft5WmOmmNb4f2jRGCjvQI2h5-BJS5r6AzAkuncAOq5otJwdEG1DLur_moEd9o25X1Dxq7qKEx-LXQL6tUR4i3CKyYbLdavi36XQCOaqRLKIDRybrXeLvnV8-R1RND_v9XCKW_VnmjcvpOOlc6dKrl1gA7PXtwdOIM0C4-rG_3C5eaxigiZe87SfO5k9Du7vaVtCbgYLXE4ZhJNbWb_VhcqEBw7E1yWelUerQGzHopUl_2PYIadOSH4DzEf5ZFJbD8bF_egsuszdMmEJ81P73aLJKouo94gK2sKNr9Br4NWiQ9xg1tQytsUaRTrEi9BPbSjXMCRW0KPdAO2eODysMEh2ryLuNE-pySXargcQytpL5yJUSaVNbEm38IeX6bBs3lLc7AWTabj2rjcaGu0O1lAt01qMy7xPZ0IepO5Bc3y_n_DsYS7aTpldSOVqnKC1kn7uCDdPcfBcXCe7hDKgZzf1hRJwqIeGnDSJpF4kIHG1aABHmQlV5SLe5D2IAleI7jXaDn7-l0ect13iJbitpAjAFNr4Mrl1oXS4N6sA4g9lWft4YiHJjIRY8D0a6VA8r1qErxBSl_N-ybk=w898-h673-no[/IMG]

---

### Post by RobGoss on 2016-05-25
Hello and welcome to the forum, how did you create your installation are you using a USB in order to boot from?

---

### Post by KloudAlpha on 2016-05-25
I created a USB installer with Unetbootin and installed it to a spare hard drive.

---

### Post by RobGoss on 2016-05-25
Seeing this is a new installation you don't have anything to loose I recommend trying a new installation

If you only have access to Windows try [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) to create your **bootable USB** that's what I also use and it works great each and every time, it's worth a shot, I would also download another ISO file just in case there's some issues with the one you are using.

Here's how you can check to make sure your ISO file is up to standards [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Sometimes with Ubuntu not every installation will go smoothly so when I have trouble in the beginning of a new installation I always download another ISO file and do a cleans install.

It could be a number of things but this is a good starting point I think

---

### Post by KloudAlpha on 2016-05-25
"new installation"

not very new to me. I spent an entire day trying to make a theme and all the other customization options to my liking, installed all kinds of stuff and now I just have to reinstall it for no reasons? 

back to windows i guess.

---

