---
title: "Is it possible to access the root area of an Android phone from Ubuntu?"
date: 2015-08-02
forum: General Help
---

### Post by Robbyx on 2015-08-02
The android phone is connected to Ubuntu by usb. I can see the sd drives internal and external, but no the system area. Can I access the system area from the ubuntu computer?

---

### Post by ian-weisser on 2015-08-02
The phone is not a dumb storage media. It's a clever computer emulating a dumb storage media for your convenience.
You must root and instruct the phone to allow Ubuntu to see what you wish.

---

### Post by Robbyx on 2015-08-02
I have rooted my phone, as for telling the phone to allow Ubuntu to see what I wish, that was really my question. Of course I went in to the phone having root access for Ubuntu, but that did not work for the phone. Are there some steps I should follow to enable access of the phone's root system  via a usb connection from  Ubuntu?

---

### Post by PhilGil on 2015-08-02
> **Robbyx said:**
> I have rooted my phone, as for telling the phone to allow Ubuntu to see what I wish, that was really my question. Of course I went in to the phone having root access for Ubuntu, but that did not work for the phone. Are there some steps I should follow to enable access of the phone's root system  via a usb connection from  Ubuntu?

You also need to be sure your phone is connected to the computer in USB debugging mode. That option should be available when you plug your phone into the computer.

If you've rooted your phone but not installed a custom ROM, USB debugging may not be available until you enable Developer Options. This varies by phone and Android version, so you'll have to Google it. It's a menu item in older Android versions. In newer versions it typically involves multiple taps on one of the items in the About Device menu.

---

### Post by Robbyx on 2015-08-02
I did notadvise  that i have installed a CW11 rom. I tried to obtain access to the root area with the new CW11 and kernel installed. I could access the SD drives via a USB connection, but could not find a way into the root of the phone from Ubuntu. In fact I could not even see the root section of the phone from Ubuntu. Any ideas as to how it is done?

---

### Post by PhilGil on 2015-08-02
OK, let's start at the beginning. Getting access to an Android device's root storage from a PC is a bit complicated.

In newer versions of Android (including CM11), the default file access is through the MTP protocol. This is the default method that Ubuntu uses to connect to your phone, and you only have access to media storage. This is by design from Google. I think it sucks, but it is what it is.

In order to access the root storage of you device from Ubuntu, you need to enable Developer Options. I thought this was enabled by default in Cyanogenmod, but I could be wrong. In any case, if you do not have a Developer Options menu in your settings you need to enable it. Use Google to find out how to do that.

Once Developer Options are enabled, you need to enable USB debugging mode. This is a menu item in the Developer Options menu. I'd suggest re-booting the phone after you've completed this step.

After completing these steps, plug your phone into your Ubuntu computer. Your should get a prompt, on your phone, asking you if you want to connect using USB Debugging Mode. Accept, and you'll have access to your entire device from the Ubuntu desktop.

It's been a while since I've tested it, but instead of screwing around with developer options, you may also be able to use AirDroid to get into your file system on a rooted phone.

---

### Post by gdesilva on 2015-08-02
I thought the ADB shell will allow access to a phone once root access is granted?

---

### Post by PhilGil on 2015-08-02
> **gdesilva said:**
> I thought the ADB shell will allow access to a phone once root access is granted?
ADB will work, if you're comfortable with the command line and all you need to do is move a few files back and forth. I could be wrong, but I was making the assumption that the OP wanted file browser access to his/her phone.

---

### Post by Robbyx on 2015-08-03
Yes, I wanted browser access because then I can see what I am moving. Phil, thank you for the advice.

Robin

---

### Post by leunam12 on 2015-08-04
> **PhilGil said:**
> OK, let's start at the beginning. Getting access to an Android device's root storage from a PC is a bit complicated.

In newer versions of Android (including CM11), the default file access is through the MTP protocol. This is the default method that Ubuntu uses to connect to your phone, and you only have access to media storage. This is by design from Google. I think it sucks, but it is what it is.

In order to access the root storage of you device from Ubuntu, you need to enable Developer Options. I thought this was enabled by default in Cyanogenmod, but I could be wrong. In any case, if you do not have a Developer Options menu in your settings you need to enable it. Use Google to find out how to do that.

Once Developer Options are enabled, you need to enable USB debugging mode. This is a menu item in the Developer Options menu. I'd suggest re-booting the phone after you've completed this step.

After completing these steps, plug your phone into your Ubuntu computer. Your should get a prompt, on your phone, asking you if you want to connect using USB Debugging Mode. Accept, and you'll have access to your entire device from the Ubuntu desktop.

It's been a while since I've tested it, but instead of screwing around with developer options, you may also be able to use AirDroid to get into your file system on a rooted phone.

This doesn't work for me. I have a rooted phone and debugging mode enabled but when I connect to the PC all I have access to is the internal and the external cards. I don't get any prompts on my phone.

There are three ways in which I could transfer system files to my computer.

1-ADB
2-Total Commander. I mount a shared folder on my computer in Total Commander and transfer from the phone to the PC (pushing from the phone to the PC)
3-Total Commander. Transfer the Files that I need to the SD card and then stick the card in the PC.

---

