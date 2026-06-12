---
title: "bash: quake2: command not found"
date: 2007-01-10
forum: General Help
---

### Post by JarG0n on 2007-01-10
Help!

Each time I copy an executable into /usr/local/games/ and I chmod +x to make it executable, I get the following

bash: quake2: command not found

In this case, quake2.  I also had one other instance like this.

I verified this executable exists in this directory, and that the permission is executable for the "Others" group. ](*,) 

What am I doing wrong?

---

### Post by rattking on 2007-01-10
hello 
/usr/local/games/ is not in your path 
quake4 gets around this by making a symlink in /usr/local/bin
witch is in your path

eg.
ln -s /usr/local/games/quake2/quake2 /usr/local/bin/quake2
not sure about the actual file names..

---

### Post by schilcha on 2007-01-10
Is your PATH-environment variable set up properly?

Try:
```
echo $PATH
```
and see whether /usr/local/games is included. If not, execute
```
export PATH=$PATH:/usr/local/bin
```
If that solves your problem, you might want to include that line in your .bashrc or .bash_profile or .profile or whatever files bash sources upon start-up (see man bash for the correct location)

Good luck!

---

### Post by taurus on 2007-01-10
Or just add that path to your PATH in ~/.bashrc.

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Then add the following two lines to the end of it.

```
PATH=$PATH:/usr/local/games
export PATH
```
Save it.  Log out and back in again and see if you can run your game in /usr/local/games/ now.

---

