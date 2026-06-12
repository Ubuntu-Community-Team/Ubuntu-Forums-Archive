---
title: "Run script without sudo passwd"
date: 2008-07-01
forum: General Help
---

### Post by jmasgalas on 2008-07-01
I am trying to run a script at startup that requires sudo priviledges. What is does is run the smbmount command to mount a network drive. How can I run this without sudo passwd? I edited sudoers and tried both these lines: 

jmasgalas ALL=NOPASSWD: /usr/bin/smbmount
jmasgalas ALL=NOPASSWD: /home/jmasgalas/mountscript


It still does not work. Here is the exact command in the script:

sudo smbmount //server/share /mnt/H -o username=xxxx,password=xxxx,file_mode=0777,dir_mode=0777

What am I doing wrong?

---

### Post by KenBW2 on 2008-07-01
Why do you want to run without sudo? If the script needs to access root files then it'll need sudo privileges.

---

### Post by jmasgalas on 2008-07-01
I want it to run on startup. Right now it does not work because it needs sudo priviledges.

---

### Post by caljohnsmith on 2008-07-01
> **jmasgalas said:**
> I am trying to run a script at startup that requires sudo priviledges. What is does is run the smbmount command to mount a network drive. How can I run this without sudo passwd? I edited sudoers and tried both these lines: 

jmasgalas ALL=NOPASSWD: /usr/bin/smbmount
jmasgalas ALL=NOPASSWD: /home/jmasgalas/mountscript


It still does not work. Here is the exact command in the script:

sudo smbmount //server/share /mnt/H -o username=xxxx,password=xxxx,file_mode=0777,dir_mode=0777

What am I doing wrong?
You actually don't need to mess with modifying your sudoers file in this case; if you want to run any commands/scripts on startup as root, just stick them in your /etc/rc.local file. All commands/scripts in rc.local get executed as root, so no need to put sudo in front of them in that file.

Also, if you haven't done it all ready, I would first try that smbmount command out on the command line to make sure you have it exactly right. :)

---

### Post by iaculallad on 2008-07-01
Try to make your script executable

```
sudo chmod +x <script_name>
```

Copy the script to /etc/init.d directory.

```
sudo cp <script_name> /etc/init.d
```

Execute the update-rc.d <script_name> defaults command as root

```
update-rc.d <script_name> defaults
```

---

### Post by karasuman on 2008-07-01
I have a script to connect to my bluetooth mouse.  Ordinarily, the command is sudo hidd -s, after which I have to input my password.  The script I wrote, however, does it for me, so this might work for you:

```
sudo hidd -s &&
mypassword
```

This doesn't work in an application launcher, but running the file path to the script in the launcher does connect my mouse (I just have to type /home/beth/etc. to run it, or actually double-click on it, instead of typing sudo hidd -s $$ mypassword as the command to run with the launcher.)

Give that a try.  I hope it works.  :)

---

