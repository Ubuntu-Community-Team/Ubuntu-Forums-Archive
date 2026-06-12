---
title: "How can a script display a message on the screen when started as root from incrontab"
date: 2018-08-05
forum: General Help
---

### Post by Paddy Landau on 2018-08-05
Using version 18.04, both Ubuntu and Lubuntu.

[LIST]
[*]I have a script that starts from root's incrontab (it must be root).
[*]The script needs to feed an error message to the user.
[*]Ideally, it should work whether the user is using the console or the usual desktop GUI.
[/LIST]
I've tried using notify-send and zenity, but they don't display on the screen.

How can I reliably feed the message to the user?

---

### Post by Paddy Landau on 2018-08-06
I've discovered the answer.

Using "[FONT=lucida console]who[/FONT]", find the username and the display number. In the following, I'm the only user logged into the X terminal on [FONT=lucida console]tty1[/FONT] with display :0.
```
[COLOR=#222222]$ LC_ALL=POSIX who | grep -E ' tty[0-9]+ .* \(:[0-9]+)$'[/COLOR]
paddy    tty7         Aug  6 06:58 (:0)
```
(The purpose of [FONT=lucida console]POSIX[/FONT] is so that further commands, such as "[FONT=lucida console]cut[/FONT]", perform reliably across all systems.)

The command to display on the user's terminal needs both the username and the display. In this example, I've used [FONT=lucida console]notify-send[/FONT], but you can use other GUI applications such as [FONT=lucida console]zenity[/FONT].
```
DISPLAY=${USERDISPLAY} sudo --user=${USERNAME} notify-send --urgency=critical 'Error' 'Attend to this error straightaway'
```
For example
```
DISPLAY=:0 sudo --user=paddy notify-send --urgency=critical 'Error' 'Attend to this error straightaway'
```

**EDIT:** notify-send ignores the DISPLAY variable, and so it is unfortunately unreliable. Best to use something like zenity or [yad]("https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager").

---

