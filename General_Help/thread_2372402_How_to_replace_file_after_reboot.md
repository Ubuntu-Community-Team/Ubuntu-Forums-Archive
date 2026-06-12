---
title: "How to replace file after reboot?"
date: 2017-09-24
forum: General Help
---

### Post by heureux2 on 2017-09-24
Hello all,


I have a problem now that how to replace file after reboot?

I mean I want to write a *.sh file which can replace the certain file after reboot and before login to the ubuntu system. 

This process likes the windows system make system hotfix after reboot.


Could anyone give me some tips?

Thanks.

---

### Post by wildmanne39 on 2017-09-25
Welcome to the forum! *Thread moved to **General Help for a better fit**.*

---

### Post by efflandt on 2017-09-25
It depends what you want the script to do and whether it requires anything else to be up and active before it happens. If it does not require anything specific (like networking, etc.) to first be enabled, you can edit and add, or create if it does not exist, **/etc/rc.local** and give it execute permission. Note that during boot if that file is executable, anything in it will run as root, but with minimal environment. So you should use a full path to the script and full paths (to commands or files) for anything you do in the script.

If it does require that something else be up before it runs, you may need to look into how boot scripts are handled in sequence for your particular Ubuntu version.

Note that file extensions don't really matter for scripts, so having .sh extension is just for your own convenience, so you know that it is a shell script.

---

### Post by heureux2 on 2017-10-14
Thanks for your help.;)

---

