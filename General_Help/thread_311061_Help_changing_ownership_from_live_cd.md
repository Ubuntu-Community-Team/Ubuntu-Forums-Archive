---
title: "Help changing ownership from live cd"
date: 2006-12-02
forum: General Help
---

### Post by vikrant_me on 2006-12-02
I need to change the ownership of a file i have created a user vicky now when i type:

ubuntu@ubuntu:~/Desktop/1/home/vicky$ sudo chown -R 0755 vicky:vicky /home/ubuntu/Desktop/1/home/vicky
chown: cannot access `vicky:vicky': No such file or directory

                 I get the above error, i am running a live cd and it probably does not know of the existence of a user named vicky besides user ubuntu.

---

### Post by Kurt` on 2006-12-02
You're trying to combine 2 seperate commands, try these:

sudo chown -R vicky:vicky /home/ubuntu/Desktop/1/home/vicky
sudo chmod -R 0755 /home/ubuntu/Desktop/1/home/vicky

The first changes the user/group that owns the directory (and all subdirectories/files), and the second sets the directory (and all subdirectories/files) to be readable, writable, and executable by the user that owns them, and readable/executable by everyone else.

There still won't be a user "vicky" on the LiveCD (as you correctly mentioned), and since I'm not sure what you're trying to do, I can't help you any more than that. Good luck.

---

