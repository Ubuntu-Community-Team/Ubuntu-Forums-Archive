---
title: "Sending strings with spaces as parameters to a function?"
date: 2015-01-23
forum: General Help
---

### Post by kieran6 on 2015-01-23
Alright so I'm about to smash my head through a wall here. After hours of messing around and searching google I couldn't find any answers to my question.

Basically I have something like this, it's an init.d script: (I've omitted some of the cases from the case statement and other codes that aren't relevant)

```
func_command() {
  command="$1"
  sudo -u server screen -S server -X stuff "$command"
}

case "$1" in
  command)
    func_command "$2"
    ;;
```

So if I was to send something along the lines of

```
service server command "this is command"
```

The desired output that should be sent to the screen is

```
this is command
```

But it appears to be simply sending this to the screen:

```
"this"
```

Just need a way to be able to send the command in its entirety. It needs to have spaces, and won't always be only 3 words long.
Seems like such a simple problem but I've been stuck on it for hours. It really bothers me.

Any help is greatly appreciated.

---

### Post by kieran6 on 2015-01-24
Figured out a solution finally:

```
[COLOR=#000000][FONT=Ubuntu Mono]func_command() {[/FONT][/COLOR]  
  command="$*"
  sudo -u [SERVER[IMG]http://cdncache-a.akamaihd.net/items/it/img/arrow-10x10.png[/IMG]]("http://ubuntuforums.org/#") screen -S [SERVER[IMG]http://cdncache-a.akamaihd.net/items/it/img/arrow-10x10.png[/IMG]]("http://ubuntuforums.org/#") -X stuff "${command#* }"
}

case "$1" in
  command)
    func_command "$*"
    ;;
```

Basically just have to send all the parameters to the function and omit the "command" word from it. Would rather the string was a single parameter, but I don't think it's going to let me do that.

---

### Post by SeijiSensei on 2015-01-24
What if you enclose the string in single quotes rather than double quotes?  Usually bash treats something like 'this is a string' as a literal.

---

### Post by kieran6 on 2015-01-29
Sorry for the slow response, I've been quite busy. I did try the single quotes but it didn't make a difference. Thank you for your response though.

---

