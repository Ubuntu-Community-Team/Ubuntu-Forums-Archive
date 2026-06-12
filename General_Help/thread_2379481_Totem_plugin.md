---
title: "Totem plugin"
date: 2017-12-06
forum: General Help
---

### Post by czgirb on 2017-12-06
I used Compaq CQ40-328TU + Ubuntu Pangolin

Yesterday I download a movie (MP4), today ... when I want to play it in my Totem, I've got the following messages
```

Required plugin could not be found
Videos requires to install plugins to play media files of the following type: video/x-gst-fourcc-hev1 decoder

```
Please guide me what should I do
Thank you

---

### Post by vasa1 on 2017-12-06
> **czgirb said:**
> I used Compaq CQ40-328TU + Ubuntu Pangolin
...
Ubuntu Pangolin desktop is no longer supported unless you sign up for commercial support
[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)
[https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/](https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/)
[http://www.zdnet.com/article/canonical-extends-ubuntu-12-04-support-for-paying-customers/](http://www.zdnet.com/article/canonical-extends-ubuntu-12-04-support-for-paying-customers/) and from the third link> ... if you can't update before Ubuntu 12.04's LTS period ends on Friday, April 28, 2017, you can purchase an Ubuntu 12.04 Extended Security Maintenance (ESM) license. Unlike the newer versions of Ubuntu, these updates won't be free.

Instead, Ubuntu 12.04 patches will be available only through the Ubuntu Advantage support plan. Prices start at $150 per year per server and $250 per year with a minimum of 10 virtual servers. The latter plan includes work week online and phone technical support. There's also a desktop plan, which will run you $150 per year per desktop with a minimum order of 50 desktops. These updates will be delivered in a secure, private archive available only to customers on a per-node basis. ...

---

### Post by czgirb on 2017-12-06
> **vasa1 said:**
> Ubuntu Pangolin desktop is no longer supported unless you sign up for commercial support
[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)
[https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/](https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/)
[http://www.zdnet.com/article/canonical-extends-ubuntu-12-04-support-for-paying-customers/](http://www.zdnet.com/article/canonical-extends-ubuntu-12-04-support-for-paying-customers/) and from the third link

**[SIZE=5]SORRY[/SIZE]** ... it's not pangolin. it's **[SIZE=5]14.04[/SIZE]** or **[SIZE=5]Trusty Tahr[/SIZE]**

---

### Post by Yellow Pasque on 2017-12-06
[https://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux](https://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux)

Basically:
```
sudo apt-add-repository ppa:strukturag/libde265
sudo apt-get update
sudo apt-get install gstreamer1.0-libde265
```

Now, Totem should be able to play HEVC content.

---

### Post by czgirb on 2017-12-06
> **Temüjin said:**
> [https://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux](https://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux)

Basically:
```
sudo apt-add-repository ppa:strukturag/libde265
sudo apt-get update
sudo apt-get install gstreamer1.0-libde265
```

Now, Totem should be able to play HEVC content.

Do it ... play the film and show up this messages:
```
An error occurred
Overflow in input data, check data mode
```

---

### Post by Yellow Pasque on 2017-12-06
Have you tried other HEVC videos to rule out the possibility of a poorly encoded video?

---

