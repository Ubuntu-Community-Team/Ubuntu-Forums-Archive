---
title: "Video Problems Compaq Desktop"
date: 2017-04-04
forum: General Help
---

### Post by aviator1 on 2017-04-04
I'm posting for a friend who just downloaded 16.04 to his Compaq Desktop.

He says that it boots fine, but shortly after getting a desktop, and sometimes after clicking to open a program, that the screen just fills up with colored lines all over.

As I recall, Compaq had some of their own hardware mixed in the computer?

Any ideas?

Let me know what info I need to gather.

Thanks.

---

### Post by gordintoronto on 2017-04-04
Here's how I gather useful information:

cd Desktop
sudo lshw -html >compaq.htm

The issue probably relates to the video adapter, and that will be identified. He might also try a different Linux version, such as Xubuntu 17.04, which will be released soon.

---

### Post by aviator1 on 2017-04-05
Thanks. I will talk with him tomorrow and report.

---

