---
title: "How to preserv user id/previleges while root in a bash script."
date: 2014-04-08
forum: General Help
---

### Post by octius4u on 2014-04-08
Hi everybody.

I've tried to google for answers first but without any luck, so if I missed an answer please excuse and redirect me.

**My Situation**
I'm writing an post-install tweak script in /bin/bash, and because I don't want to have 15 sudo's and
be asked for the password to many times etc. I'm running it as root ```
sudo bash MyPostTweaks.sh
```

The script looks basically like this:

```
#!/bin/bash
apt-apt-repository -y $ppa_one
apt-get update 
apt-get install -y $app_one

#Now some tweaks for the user
wget $WebAddress --directory-prefix=$HOME/Pictures
# or something like
cp ../myconfs/myapp2.conf $HOME/.config/myapp2/


```
[B]
Now my Problem[/B]

I have had problems where programs have worked badly, by not having permissions, or even worse even though the *.desktop was install and present /usr/share/applications clicking on it would not work. I began to notice whats wrong because it tried to run the program from the terminal and read some error messages. The same problem was not present if I stated the program from a second user account. I understand that the reason for the permissions/privileges issues is the script being ran as root. I also know about sudo chmod or sudo chown but since I don't know where the issue lies because I've even tried ```
sudo chmod -R 755 ~/* && sudo chown -R octius4u:octius4u ~/*
```.

**My Question**

While in user octius4u i run the script as sudo bash MyPostTweaks.sh essentially putting me in root's account. If I run the script on a computer where the user name has changed, for example because I got bored of the old user name, how can I determine it? 
In order to run some thing like ```
sudo -u $NormalUser cp ../myconfs/myapp2.conf $HOME/.config/myapp2/
``` Can I use or combine some of the following commands?

w
id -un
whoami
in order to get something similar to ```
if [ $w_user = $(id -un) ]; then; sudo -u $w_user cp $path/$file /$newpath
```

Thank you in advance for any help or insights you can provide.

---

### Post by Lars Noodén on 2014-04-08
You should be able to determine the original user's account with the environment variable SUDO_USER.  That's the only one I can find that contains the original account, along with SUDO_GID and SUDO_UID.

---

### Post by octius4u on 2014-04-08
I think that would work great! Thank you very much.

Would you know how to determine the $SUDO_USER's home path? 
I am asking because i know that in some cases the home directory is not just /home/octius4u but it could be /home/o/octius4u or something else.

---

### Post by Lars Noodén on 2014-04-08
The only way to be sure would be to poll /etc/passwd to find what is really set there:

```

h=$(awk -F ':' "\$1==\"$SUDO_USER\" { print \$6 }" /etc/passwd);
echo $h

```

Mind all the escapes.  The shell doesn't make it easy to work with $ and " inside strings.  The field separator is set to a colon so that /etc/passwd makes sense to the rest of awk.

Edit: be sure to check that $h is not empty before trying to use it in path to do something automatic..

---

### Post by octius4u on 2014-04-08
I have entered echo $h before running your code and it was empty and after your code it did contain the correct user path even if it was enter from within root.
Even if I am not (yet) familiar with awk I can use it by simple copy and pate (for now) and it seems to work just perfectly. 

I consider my question answered and my problem solved.

_**You have help me a lot. Thank you very much.**_

---

### Post by Lars Noodén on 2014-04-08
Glad it saved time.  awk is simple once the main concept is understood: it's a bunch of if-then statements, but the now traditional markers are left out.  In pseudo code here is the same bit

```

set field_separator to ':'

read /etc/passwd through to the last line

split each line into fields separated by ':'

if the first field of a line equals the value "$SUDO_USER" then print the content of the sixth field

```

It's great for very short scripts or one-liners.  Anything more and you probably need perl or python.

---

### Post by octius4u on 2014-04-08
If you don't mind, I have a related question.

Regarding installing new ppa's I wish to make sure that the ppa address isn't already installed. 
Could I use awk verify if it already exists, or would there be a easier way?

---

### Post by Lars Noodén on 2014-04-08
[grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html) might work as an even simpler test.

```

grep -rl '^deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu' /etc/apt/* 2>/dev/null

```

That's a search for an exact string at the beginning of the line.  

The files to look in would be in /etc/apt/ or /etc/apt/sources.list.d/ and they would contain the pointer to the PPA or not, the -r makes the search recursive. 
Directories can't be grepped so they make noise (warnings) so 2> redirects stderr to /dev/null

---

### Post by octius4u on 2014-04-08
I have looked up "/dev/null" [here]("http://askubuntu.com/questions/350208/what-does-2-dev-null-means") at askubuntu.com and [here]("https://stackoverflow.com/questions/12363916/if-dev-null") at stackoverflow.com
Would the following therefor be correct?

```
grep -rl '^deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu' /etc/apt/* 2>/dev/null


if [ $(/dev/null) = "0" ]; then
      # Adding new ppa's
else
      echo "it exists already"
fi
```

---

### Post by Lars Noodén on 2014-04-08
The variable to test after the fact would be $?

But you can run the test directly on grep itself.

```

if ! grep -rl '^deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu' /etc/apt/* 1>/dev/null 2>&1;  then
      # Adding new ppas
else
      echo "it exists already"
fi

```

To cut down on the noise in the script, 1 is stdout, 2>&1 sends stderr to stdout, which is getting sent to the bit bucket (/dev/null).

---

### Post by octius4u on 2014-04-08
You've helped me with more than just my initial problem. Therefor **THANK YOU** very much. Now it is up to me to study, dissect, understand and integrate. 

Later when I'm done with it all of it, I'd like to get some constructive criticism on the hole script, since it's my first complex script. I just don't know: 

- if it is something like this is done, 
- the proper site, 
- category or section, 
- conditions etc. 

It would be just great if I could get some opinions, but even if not, **I am very grateful**.

---

