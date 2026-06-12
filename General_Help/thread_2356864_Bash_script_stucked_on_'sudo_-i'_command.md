---
title: "Bash script stucked on 'sudo -i' command"
date: 2017-03-27
forum: General Help
---

### Post by aguilasainz on 2017-03-27
Hi there,

I'm working on a bash script, and it's almost done, there's only one problem while I'm using a 'sudo -i' command, here goes the line:

```
sudo -i PYTHONPATH=/usr/local/lib/python2.7/dist-packages/
```
*As you will know, the PYTHONPATH won't work without the -i option.


The issue is that the script get stuck in the root's shell, as seen here:

```
gsm@gsm:~$ bash script 
root@gsm:~# 

```
And if I type 'exit', it will go out and continue with everything.

Any tips to solve this 'stuck' thing?

Thank you!

---

### Post by aguilasainz on 2017-03-27
[SOLVED]

Replacing the original line with this one, solves the problem:

```
sudo bash -c "[COLOR=#000000][FONT=&quot]PYTHONPATH=/usr/local/lib/python2.7/dist-packages/"[/FONT][/COLOR]
```

---

