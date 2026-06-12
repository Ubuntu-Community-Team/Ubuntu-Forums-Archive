---
title: "How to &quot;source&quot; file.sh &quot;for ever&quot;?"
date: 2014-07-24
forum: General Help
---

### Post by jan26 on 2014-07-24
I am working with **Xilinx ISE 14.6** programming environment on my **64 bit Ubuntu 14.04 LTS**. Before I run it I have to log in as root and source one file:

```

sudo -s
source settings64.sh

```

The problem is, that I have to do this every time. Is there any possibility to source once and do not worry about this any more?

---

### Post by sudodus on 2014-07-24
If you add it to your **~/.bashrc** file it will be run whenever you start a terminal window. But you must enter your password (sudo needs it). If you add it (without sudo -s) to
[B]
/etc/bash.bashrc[/B] I think it will be run once and will be set for all users and all terminal windows. Would that be OK?

---

### Post by jan26 on 2014-07-24
[B]@sudodus

[/B]Could you show me how to do this? I am new in Linux.

---

### Post by sudodus on 2014-07-24
- Start a terminal window

- Make a backup copy of the file

```
sudo cp -p /etc/bash.bashrc  /etc/bash.bashrc0
```

- Use a text editor

```
sudo nano /etc/bash.bashrc
```

- Add the following line to the end of the text (and press Enter to get a line feed at the end of the added line)

```
source settings64.sh
```

- Write and exit from the text editor. I show ***nano*** here, you might prefer another editor.

- Reboot and check that it works.

This would be convenient, but may cause problems, and I don't know what is in the script, so if it does not work, you should restore from the backup file

```
sudo cp -p /etc/bash.bashrc0  /etc/bash.bashrc
```

and add the following lines to ~/.bashrc instead. Cut and paste from my post here into the text editor.

Backup:

```
cp -p ~/.bashrc ~/.bashrc0
```

Start the editor

```
nano ~/.bashrc
```

Enter these lines to the end of the text. Finish with enter to get a newline.

```

read -p "Development environment (y/n)" ans
if [ "$ans" == "y" ]
then
 sudo -s
 source settings64.sh
fi

```

And you must enter password each time you answer 'y' and want the development environment.

---

### Post by jan26 on 2014-07-24
The first option does not work for me.

The root option keeps asking;


```

Development environment (y/n) y
```

And i have to abort this with ctr + c.

---

### Post by steeldriver on 2014-07-24
Can we take a step back here - why are you using root? Are you saying there's something in your settings64.sh file that needs root permission in order to run it - or are you doing you actual development in a root environment?

Either way I can't help feeling there's a better way of achieving your end goal here

---

### Post by jan26 on 2014-07-24
All right.

At the end of the installation i was ordered to follow this command:
```
. /opt/Xilinx/14.6/ISE_DS/settings64.sh
```

Everything if fine with this except of licensing. It simply does not see my license, that was installed properly.

When i source this as root and then open ISE:
```
sudo -s
source /opt/Xilinx/14.6/ISE_DS/settings64.sh

```
Problem disappears and everything works well.

ISE was installed using root of course. License Manager appeared during installation, so probably was opened by root. Can it cause problem that program was licensed by root, not by user?

---

### Post by steeldriver on 2014-07-24
Well I would focus on fixing the underlying (permissions?) problem, rather than brute forcing things with root - it's almost always the wrong way to do things

According to [this SO answer]("http://stackoverflow.com/a/15132340") it should only be necessary to run the setup64.sh once, and as your regular user. Perhaps if you ran it via sudo the first time it left some root-owned files which are now preventing subsequent runs with normal user rights?

---

### Post by jan26 on 2014-07-24
[B]@steeldriver
[/B]
First time I did not run it via sudo, but via user.

I tried to do this according to SO answer

```

[COLOR=#00ff00]jan@jan[/COLOR]:~$ cd /opt/Xilinx/14.6/ISE_DS
[COLOR=#00ff00]jan@jan[/COLOR]:[COLOR=#0000cd]/opt/Xilinx/14.6/ISE_DS[/COLOR]$ chmod u+x *.csh *.sh
chmod: changing permissions of &#8216;settings32.csh&#8217;: Operation not permitted
chmod: changing permissions of &#8216;settings64.csh&#8217;: Operation not permitted
chmod: changing permissions of &#8216;settings32.sh&#8217;: Operation not permitted
chmod: changing permissions of &#8216;settings64.sh&#8217;: Operation not permitted
[COLOR=#00ff00]jan@jan[/COLOR]:[COLOR=#0000cd]/opt/Xilinx/14.6/ISE_DS[/COLOR]$ sudo chmod u+x *.csh *.sh
[sudo] password for jan: 
[COLOR=#00ff00]jan@jan[/COLOR]:[COLOR=#0000cd]/opt/Xilinx/14.6/ISE_DS[/COLOR]$ . /opt/Xilinx/14.6/ISE_DS/settings64.sh
. /opt/Xilinx/14.6/ISE_DS/common/.settings64.sh /opt/Xilinx/14.6/ISE_DS/common
. /opt/Xilinx/14.6/ISE_DS/EDK/.settings64.sh /opt/Xilinx/14.6/ISE_DS/EDK
. /opt/Xilinx/14.6/ISE_DS/PlanAhead/.settings64.sh /opt/Xilinx/14.6/ISE_DS/PlanAhead
. /opt/Xilinx/14.6/ISE_DS/ISE/.settings64.sh /opt/Xilinx/14.6/ISE_DS/ISE
[COLOR=#00ff00]jan@jan[/COLOR]:[COLOR=#0000cd]/opt/Xilinx/14.6/ISE_DS[/COLOR]$ ise




```


Still problem with license. I can work with ISE running it as root. I just wanted to make it easier.

---

### Post by sudodus on 2014-07-24
> **jan26 said:**
> The first option does not work for me.

The root option keeps asking;


```

Development environment (y/n) y
```

And i have to abort this with ctr + c.

- Do you reply y (and press Enter)?

- And after that enter the password to run sudo?

In that case maybe the script is such, that it should be run directly from the terminal, and you should restore also the original **~/.bashrc**

```
 cp -p ~/.bashrc0 ~/.bashrc
```

Could you restore both files? **/etc/bash.bashrc** and **~/.bashrc** And reboot?

Maybe the best alternative is to ask those who make or sell the software, if there is an easier alternative than to type those two commands. We don't know what it in the script, so we can only guess how it can be automated.

---

### Post by steeldriver on 2014-07-24
There's a Xilinx forum post here suggesting the issue of non-root execution may be related to a QT_PLUGIN_PATH setting

> Type unset QT_PLUGIN_PATH before running ise or xsetup.

[http://forums.xilinx.com/t5/Installation-and-Licensing/Xilinx-ISE-Webpack-will-only-run-as-root-in-KDE-Slackware-64-14/td-p/287769](http://forums.xilinx.com/t5/Installation-and-Licensing/Xilinx-ISE-Webpack-will-only-run-as-root-in-KDE-Slackware-64-14/td-p/287769)

---

### Post by jan26 on 2014-07-24
Still does not work.

I read that 
```
unset QT_PLUGIN_PATH
```
should be typed before installation. 

Do you thing that removing ISE and installing it once again with typing this command before make sense if I can run it via root? 

Anyway thank you guys very much for your help :grin:

---

