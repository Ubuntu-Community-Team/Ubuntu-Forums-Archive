---
title: "copy directory via ssh to server (not home folder)"
date: 2008-04-22
forum: General Help
---

### Post by Bjerrum on 2008-04-22
Hi

I try to copy files from my laptop to my ubuntu server. It's working like this:

[FONT="Courier New"]sudo scp -r /home/name/dir_to_copy sudo name@192.168.1.2:~/.[/FONT]

But I like to update a directory which is not in the home folder like this:

[FONT="Courier New"]sudo scp -r /home/name/dir_to_copy sudo name@192.168.1.2:~/usr/local/dir_to_place_in[/FONT]

After typing password I got this:
 
[FONT="Courier New"]scp: /home/name/usr/local/dir_to_place_in/: No such file or directory[/FONT]

What am I doing wrong?

---

### Post by tjajab on 2008-04-22
Remove the tilde (~). ~ is an abbreviation for your home folder.

sudo scp -r /home/name/dir_to_copy sudo name@192.168.1.2:/usr/local/dir_to_place_in

should work.

---

### Post by Bjerrum on 2008-04-22
Yes. Thanks it works!

I past it in a file and run it like this:
[FONT="Courier New"]sh myscript.sh[/FONT]
I begin to see the advantage of using the terminal. :)

---

### Post by duckville on 2008-04-22
why are you using sudo?
the folders to be copied are in your ~/ so you probably have rwx access to them.

just a thought.

---

### Post by Nepherte on 2008-04-22
There is indeed no need for sudo here.

---

### Post by Bjerrum on 2008-04-22
Okay so it ends like this:
[FONT="Courier New"]scp -r /home/name/dir_to_copy name@192.168.1.2:/usr/local/dir_to_place_in/[/FONT]
and it works. Thanks

---

### Post by Joeangin006 on 2008-12-06
> **tjajab said:**
> Remove the tilde (~). ~ is an abbreviation for your home folder.

sudo scp -r /home/name/dir_to_copy sudo name@192.168.1.2:/usr/local/dir_to_place_in

should work.

Hello Mr Tjajab
I have a little problem in my Ubuntu:
1. I've installed xampp in my Acer4520.
2. I want to copy my project directory (myweb) to /opt/lampp/httdocs, but command paste is nactive when i put mouse in dir (opt/lampp/httdocs).

Can you explain what would I do?
Thanx

---

