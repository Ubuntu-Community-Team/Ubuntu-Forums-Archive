---
title: "a problem occurred when checking for updates ubuntu"
date: 2015-08-07
forum: General Help
---

### Post by pubudup on 2015-08-07
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]My screen has a red circle with a white line through it on the top right hand corner with the above error message. I'm running 14.04 LTS. Please help.

Regards,
Pubudu.[/COLOR]

---

### Post by bapoumba on 2015-08-07
Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
```

How to use code tags to post long outputs : [http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code](http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code)

---

### Post by mtgran on 2015-09-03
> **bapoumba said:**
> Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
```

How to use code tags to post long outputs : [http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code](http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code)

Hi, 

I am having the same problem concerning the checking for updates , here are the outputs:

cat -n /etc/apt/sources.list  -> [http://paste.ubuntu.com/12270355/](http://paste.ubuntu.com/12270355/)
ls -la /etc/apt/sources.list.d  -> [http://paste.ubuntu.com/12270362/](http://paste.ubuntu.com/12270362/)
tail -v -n +1 /etc/apt/sources.list.d/*  -> [http://paste.ubuntu.com/12270371/](http://paste.ubuntu.com/12270371/)
sudo apt-get update  -> [http://paste.ubuntu.com/12270390/](http://paste.ubuntu.com/12270390/)
sudo apt-get upgrade  -> [http://paste.ubuntu.com/12270397/](http://paste.ubuntu.com/12270397/)


Any idea?

Regards and thanks in advance

---

### Post by mtgran on 2015-09-04
Solved, symbolic link to python3.4" was lost:

solution:
sudo apt-get --reinstall install python3-minimal

---

