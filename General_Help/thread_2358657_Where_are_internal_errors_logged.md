---
title: "Where are internal errors logged?"
date: 2017-04-15
forum: General Help
---

### Post by dean.w.schulze on 2017-04-15
I've suddenly gotten a bunch of internal errors on my new laptop today.  Where are these errors logged?  I've looked in the .log files in /var/log but none of them contain "internal error" or the specific Assertion I'm seeing in the internal error popup dialogs.

Thanks.

---

### Post by vasa1 on 2017-04-15
If you can't copy/paste the contents, please provide a screenshot. You can use the paperclip icon above the post composing area to help you add the image to your post.

I googled for ubuntu "internal error". Do any of these links help?
[https://www.bleepingcomputer.com/forums/t/557463/ubuntu-1404-has-experienced-an-internal-error/](https://www.bleepingcomputer.com/forums/t/557463/ubuntu-1404-has-experienced-an-internal-error/)
[https://unix.stackexchange.com/questions/326427/ubuntu-16-10-showing-error-after-booting-sorry-ubuntu-16-10-has-experienced-a](https://unix.stackexchange.com/questions/326427/ubuntu-16-10-showing-error-after-booting-sorry-ubuntu-16-10-has-experienced-a)
[https://answers.launchpad.net/ubuntu/+question/404433](https://answers.launchpad.net/ubuntu/+question/404433)
[http://howtoubuntu.org/how-to-disable-stop-uninstall-apport-error-reporting-in-ubuntu](http://howtoubuntu.org/how-to-disable-stop-uninstall-apport-error-reporting-in-ubuntu)

---

### Post by RobGoss on 2017-04-16
Are you receiving theses errors when you try updating your system? with out seeing the errors there's not much we can advise

---

### Post by dean.w.schulze on 2017-04-16
I submitted the error reports through the internal error dialog process, but I cannot copy the information from that dialog. You mean the error messages from that dialog aren't logged somewhere on my system?  The Assertion in the dialog was from the file present.c.  It seems to be caused by the "dim screen to save power" check box.  Unchecking that box seems to have solved the problem.

---

### Post by RobGoss on 2017-04-16
Is everything working now as it should?

---

### Post by dean.w.schulze on 2017-04-16
My laptop is no longer rebooting when the screen turns off / dims so that part seems solved.  But I need to know where internal errors are logged so I can file bug reports.

---

### Post by RobGoss on 2017-04-16
Try going to var/log/booglog I'm not sure if this will be of use but it's a start

---

### Post by dean.w.schulze on 2017-04-17
The contents have a scrollbar and can be much larger than a screen shot can capture.  Isn't this information logged somewhere?

---

### Post by vasa1 on 2017-04-17
> **dean.w.schulze said:**
> The contents have a scrollbar and can be much larger than a screen shot can capture.  Isn't this information logged somewhere?
Look at /var/log

In particular, look at /var/log/apport.log, /var/log/apport.log.1, etc

There's also /var/crash.

---

