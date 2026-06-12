---
title: "Help with zenity message on top of rdesktop in full screen"
date: 2014-07-15
forum: General Help
---

### Post by greavette on 2014-07-15
Hello,

I'm using zenity on a thin client type computer (small raspberry pi running debian).  The Thin Client computer uses rdesktop to remote into a Windows VM.  I'd like to be able to show a popup to the user and thought Zenity would work well.  I can ssh into the thin client and using the following script pop up a message on the Thin Client desktop.

```
sleep .1 && wmctrl -a Information -b add,above &
WINDOWID=$(xwininfo -root -int | awk '/xwininfo:/{print $4}') \
  zenity --display=:0.0 --info --text="This is a test" &
```

But when I have rdesktop in full screen mode the zenity popup message stays behind the rdesktop session.  If i minimuze rdesktop I can see the message so I know the zenity script is working.  

Any ideas how I can bring this popup to be in front of all windows?  If not through zenity, are there other message pop-up or even net-send type messages I can use to send a message to this thin client that the user will see?

Thank you.

---

### Post by tgalati4 on 2014-07-15
I don't think *zenity* can punch through a full-screen window.  It relies on the local window environment and rdesktop takes over.  There are several message frameworks:

```
apropos message
```

---

### Post by greavette on 2014-07-17
I think you may be right...nothing I try with zenity can show the message when rdesktop is in full screen mode.  So I did some searching to see if there is another solution.  I've tried:

*  xmessage
*  zenity
*  yad
*  wall
*  netcat
*  iptux
*  talk
*  notify-send

But no dice...all display the message behind rdesktop.

---

### Post by tgalati4 on 2014-07-17
You would need to dig into the details of rdesktop and see what frameworks are used and if any of those frameworks can be used to punch a message through.

Perhaps use Windows Messenger to send the message.  You would write a script to send a message to the Windows VM instance.

What is the purpose of the message?

---

