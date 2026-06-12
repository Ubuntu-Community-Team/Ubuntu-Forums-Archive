---
title: "Popup message using zenity &amp; crontab - can't get it working"
date: 2008-02-21
forum: General Help
---

### Post by irw on 2008-02-21
I followed the steps in this page: [Howto get enough sleep despite stumbleupon with ubuntu]("http://martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/") (my wife keeps complaining I never get to bed early enough ...)

The steps i took:
```
sudo gedit /etc/crontab
```

added these lines:```
25 23 * * 0-4   ian  /usr/bin/zenity --display :0 --warning --text="Shutting down in 5 minutes. Save all your documents, shutdown, and go get some sleep."
25 23 * * 0-4   root    shutdown -h +5
```

and saved it.

The shutdown works fine, but i get no warning message to remind me.

I have tried various combinations of editing this with "contab -e" or "crontab -u ian -e" or adding variations on the theme of "export DISPLAY=:0" - all wih no effect! ](*,)

I could try creating a script to do this - it seems that several people do that rather than directly in contrab, but i have enough scripts to confuse me already and I don't like to be beaten!

Any ideas or suggestions would be very welcome.  Thanks.
Ian.

---

### Post by irw on 2008-02-24
Bump - any ideas anyone - or is there a better category to ask this in?

---

