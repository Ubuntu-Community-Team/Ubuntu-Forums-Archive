---
title: "Can't copy files to phone"
date: 2008-06-06
forum: General Help
---

### Post by sicofante on 2008-06-06
I was happily surprised to see my Nokia E60 phone instantly recognized via Bluetooth and being able to browse the phone's content.

However, I can copy files from the phone to the desktop, but not the opposite. When trying to copy a file from the desktop to the phone I get the following message:

Operation not supported by backend

(please see attached screenshot)

Any ideas?

---

### Post by PmDematagoda on 2008-06-06
Could you please click "Show more details" and post what you get.

---

### Post by sicofante on 2008-06-06
"Show more details" is clicked already. Those "more details" are the message "Operation not supported by backend". Nothing else.

---

### Post by sicofante on 2008-06-14
I just tried another phone (a Nokia 5200) and I got exactly the same results: I can copy from the phone but not to the phone.

Maybe I'll install the 32 bit version of Ubuntu and we'll see.

---

### Post by MusicMastaMike on 2008-06-15
Exact same problem on a Samsung SHG-T729... Really would like to get this figured out so I can put some files on my phone!

---

### Post by MusicMastaMike on 2008-06-15
Good news!  I just got this to work.  Here's what I did:

1) Right click on the Bluetooth Manager icon in the notification area, click Preferences.  Go to the General tab, check both boxes under File Sharing.

2) Start up Bluetooth File Sharing (gnome-bluetooth).

3) Put the files you want in your $HOME/Public folder.

4) Bond your phone and laptop the usual way.

5) From your phone, browse your computer.  Your files should be visible, and you should be able to get them.


Hope this works for you as well!

---

### Post by sicofante on 2008-06-15
What do you mean by "2) Start up Bluetooth File Sharing (gnome-bluetooth)"?

Also, how do I browse the computer from the phone?

Anyway, this sounds like a workaround but not how it should work, right? Maybe we should open a bug report?

---

### Post by MusicMastaMike on 2008-06-15
Open a terminal and do:

```
sudo apt-get install gnome-bluetooth
```

This will put a Bluetooth File Sharing entry in your Applications>Accessories.

Yes, this may be a workaround, but it works flawlessly, so I will just continue doing this.  

I'm not sure how the Bluetooth works on on your phone.  I just go into My Devices, click on the entry for my laptop, and it takes me to the files being shared by my laptop, which I can then retrieve.

---

### Post by bzzzzz on 2008-06-20
I couldn't use this method as I do not have the facility on my phone to browse for a device and find my computer.

I did manage to send files to my phone by right clicking on the file I wanted to send to my phone and the selecting "send to".  I then chose to "send as" bluetooth" and "send to" my phone.  

After about 30 seconds the phone responds as though it has received a text message and the file is sitting in the received files folder.

Hope that helps someone.

---

### Post by fatagnus on 2008-10-29
Thank you, it worked for me. I hope there will be more useful error messages in Intrepid, something like this one got me thinking if it was a connection/hardware error.

---

### Post by jpeddicord on 2008-10-29
> **fatagnus said:**
> Thank you, it worked for me. I hope there will be more useful error messages in Intrepid, something like this one got me thinking if it was a connection/hardware error.

Intrepid has a new suite of Bluetooth tools. A lot of it is more streamlined; for example you don't have to activate services just to transfer a file. There are a few quirks, but it works pretty well.

---

