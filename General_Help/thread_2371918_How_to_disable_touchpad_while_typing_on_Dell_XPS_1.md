---
title: "How to disable touchpad while typing on Dell XPS 13 9360"
date: 2017-09-19
forum: General Help
---

### Post by tomcheah on 2017-09-19
[FONT=Ubuntu]Hi. I have a Dell XPS 13 9360 dual booted with Ubuntu LTS 16.04. [/FONT]


[FONT=Ubuntu]I was wondering how I could disable the mouse touchpad while I type. Any subtle touch to the touchpad completely throws off my typing. For example, the cursor shifts over to a random location and clicks, so then I start typing in the middle of a wrong sentence. I don’t experience this issue while I use Windows 10, however.[/FONT]


[FONT=Ubuntu]I’ve read on forums that this occurs because there are two touchpad drives installed or something. I tried a solution before, but when I changed the setting file, I was unable to boot Ubuntu and had to do a clean install. Since then, I’ve been a little more scared about changing files.[/FONT]


[FONT=Ubuntu]Are there any Dell XPS 13 9360 users out there that have figured this out?[/FONT]


[FONT=Ubuntu]Thanks.[/FONT]

---

### Post by Karolina.K on 2017-09-22
I am having the same problem on my xps 9360 running ubuntu 17.04, so following to see a solution

---

### Post by kc1di on 2017-09-22
Hello tomcheah and Welcome to Ubuntu  forums,

Which version of ubuntu are you using and which desktop?  We need to know this information to be able to help you.

---

### Post by Karolina.K on 2017-09-22
well mine is ubuntu 17.04 fully updated, and in libreoffice I notice the problem the most when writing. so the touchpad does not disable at all, all other functions of it works very good though

---

### Post by kc1di on 2017-09-22
[This page]("https://askubuntu.com/questions/869141/permanent-solution-to-disable-touch-pad-while-typing-on-ubuntu-16-04") may be of help. There are several options spoken of I've used touchpad-indicator in the past and it's worked for me.

---

### Post by Tadaen_Sylvermane on 2017-09-22
I wrote myself a little script and put it on a key combo. I find that the "Disable while typing" option in touchpad settings is pretty much worthless.

```
TOUCHPADID=$(xinput list | grep SynPS | awk '{print $6}' | awk -F= '{print $2}')
TOUCHPADSTATUS=$(xinput list-props "$TOUCHPADID" | grep "Device Enabled" | awk '{print $4}')

case "$2" in
                toggle)
                    if [[ "$TOUCHPADSTATUS" == 1 ]] ; then
                        xinput set-prop "$TOUCHPADID" "Device Enabled" 0
                    else
                        xinput set-prop "$TOUCHPADID" "Device Enabled" 1
                        synclient TapButton1=1 TapButton2=2 TapButton3=3
                    fi
                    ;;
                test)
                    if [[ "$TOUCHPADSTATUS" == 1 ]] ; then
                        echo "Active"
                    else
                        echo "Disabled"
                    fi
                    ;;
                *)
                    echo "usage ${0} ${1} toggle | test"
                    ;;
            esac

```

The test is for a conky output to show me if active or inactive.

---

