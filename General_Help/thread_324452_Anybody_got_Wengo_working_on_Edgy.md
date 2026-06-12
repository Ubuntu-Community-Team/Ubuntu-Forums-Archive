---
title: "Anybody got Wengo working on Edgy?"
date: 2006-12-23
forum: General Help
---

### Post by st14n on 2006-12-23
Does anybody got a version of Wengo working for Edgy? I've tried both 0.99 from the repos and the [latest 2.0 alpha]("http://openwengo.org/index.php/openwengo/public/homePage/openwengo/public/projectsNgDownload")  with no luck. For 0.99 the mic is not working, and for 2.0 neither the mic or output sound works. (Both works for Ekiga, for instance, so it's not a hardware problem.) Anybody with the same problem or maybe a solution?

---

### Post by st14n on 2006-12-25
After playing around with the alsamixer, I now have audio both in and out from the test call in wengo. Not exactly sure what did the trick. Maybe because I muted line-in... Anyway, this thread should be closed if no-one else experience the same problem.

---

### Post by sharperguy on 2006-12-27
I installed wengophone 2.0 from the site and when I phone all I get is garbaldygook.

---

### Post by pickarooney on 2006-12-30
I'd like to try it, but registration is impossible. I try and I try but the registration form keeps coming back with unknown errors, ostensibly because I'm typing the security code wrong. Thirty-eight times in a row, I don't think so. Does this only work with one particular browser or something?

---

### Post by st14n on 2006-12-30
> **pickarooney said:**
> I'd like to try it, but registration is impossible. I try and I try but the registration form keeps coming back with unknown errors, ostensibly because I'm typing the security code wrong. Thirty-eight times in a row, I don't think so. Does this only work with one particular browser or something?

I've done it several times for both Ubuntu (Opera 9.0 and Firefox 2.0) and Windows (IE7) and had no problems with this. You download the program, start it, click the button that says "Click here if you don't have a Wengo account", and a web page gets opened, right?

---

### Post by pickarooney on 2006-12-30
Yes, and on the page that opens there are a number of fields to fill in - name, password and a code to be typed to prevent bot creation of accounts. It seems to fail every time I type in this code.

---

### Post by st14n on 2006-12-30
I really don't have any clue why it is so. But if you like, you could send me a private message with your email address and desired nickname, and I will register it for you. But I guess you're also curios why the registration does not work for you. I suggest making another thread with a suitable title which draws attention to the ubuntu-people that might know.

---

### Post by pingvin on 2007-01-05
> **sharperguy said:**
> I installed wengophone 2.0 from the site and when I phone all I get is garbaldygook.

Fortunately, the sound and video works okay on mine, but I would love to know how you launch Wengophone? According to the website you type "LD_LIBRARY_PATH=. ./qtwengophone" each time, or there is a script in the Wengophone directory. Either way I'm left with both Wengophone and a dirty big terminal running at the same time. Is there a way to run it 'quietly'? And to create a nice little launcher button?

Many thanks in advance!

Mike

---

### Post by st14n on 2007-01-06
> **pingvin said:**
> Is there a way to run it 'quietly'? And to create a nice little launcher button?

To run it from a terminal with no output and with the wengophone process in the background, start it with```
./wengophone.sh &> /dev/null &
```That is, you start the script 'wengophone.sh' instead of 'qtwengophone', redirect all output to /dev/null (that is means showing no ouput), and send the process to the background.

If you want an entry in the menu, use the program 'alacarte' and add a entry that launches '/PATH-TO-WENGOPHONE/wengophone.sh'.

---

### Post by pingvin on 2007-01-06
That's exactly what I was looking for!
Thanks very much - now it looks a lot neater, and I've got that panel launcher I was after :) 

Mike

Edit: I had started a new thread, so I hope you don't mine, I've copied you solution there aswell. Thanks again.

---

