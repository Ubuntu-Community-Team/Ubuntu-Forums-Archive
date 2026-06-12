---
title: "how to install wvdial from the Live USB"
date: 2012-10-25
forum: General Help
---

### Post by Advait on 2012-10-25
Hi All,

I successfully installed 12.04 today using a USB stik that had the 12.04 ISO burned onto it. However, my internet connection can't work without wvdial. How do I install wvdial (and required dependencies) from from the USB onto the hard drive?

From what I've seen I just need to double click on some .deb files. Which files should I double click on and in which order?

[http://ubuntuforums.org/showthread.php?t=1567957](http://ubuntuforums.org/showthread.php?t=1567957)

This thread was helpful, but things may have changed since then and I want to make sure I click on the right files in the right order. Thanks!

Advait

---

### Post by dino99 on 2012-10-25
you should find that .deb into /var/cache/apt/archives/

 sudo dpkg -i  /var/cache/apt/archives/wvdial.deb

---

### Post by Advait on 2012-10-25
> **dino99 said:**
> you should find that .deb into /var/cache/apt/archives/
sudo dpkg -i  /var/cache/apt/archives/wvdial.deb

Thanks for the reply. But it didn't work. See attached screenshot. As I mentioned in my original message, I think dependencies need to be installed. That means multiple .deb files executed in a certain  order. See the thread link in the original message.

I'm guessing the files and order have changed since the earlier thread. That's what I need to know. Any ideas? Thanks,

Also, I have access to another Ubuntu computer that does have internet access. Can that be used to fix this?

Advait

---

### Post by Advait on 2012-10-25
> **dino99 said:**
> you should find that .deb into /var/cache/apt/archives/
sudo dpkg -i  /var/cache/apt/archives/wvdial.deb

Thanks  for the reply. But it didn't work. See attached screenshot. As I  mentioned in my original message, I think dependencies need to be  installed. That means multiple .deb files executed in a certain  order.  See the thread link in the original message.

I'm guessing the files and order have changed since the earlier thread. That's what I need to know. Any ideas? Thanks,

Also, I have access to another Ubuntu computer that does have internet access. Can that be used to fix this?

Advait

---

### Post by AlexDudko on 2012-10-25
Find these packages [here]("http://packages.ubuntu.com/"):
> libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial
and install them using command
> sudo dpkg -i package_name
one by one.

---

### Post by dino99 on 2012-10-25
im surprised as dpkg usually directly deals with such issues, it seems to me that something else is borked. Meaning some missing deb(s) but you should then get warnings/errors saying that.

so you need to download that libuniconf4.6 if it is missing on the hdd or if you cant get it elsewhere.

[http://packages.ubuntu.com/en/quantal/i386/libuniconf4.6/download](http://packages.ubuntu.com/en/quantal/i386/libuniconf4.6/download)

---

### Post by Advait on 2012-10-26
OK, I got it working. 1 time out of 10 my India Reliance 3G cellular modem will make a connection using the Ubuntu network settings (without wvdial). I got lucky and got a good connection. I quickly grabbed synaptic and then grabbed wvdial. Now that I've got wvdial installed I can now make a connection reliably each time. Yay! I'm back in business.

Thanks for your help and responses. If I wasn't able to make the connection then your instructions would have been really needed. Cheers,

Advait

---

