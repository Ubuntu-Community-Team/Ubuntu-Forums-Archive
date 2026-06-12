---
title: "Only 4 increments on screen brightness."
date: 2012-11-19
forum: General Help
---

### Post by goldfish777 on 2012-11-19
I saw this issue addressed elsewhere but I never actually found the answer. I have a Dell XPS 15 L502x. My screen brightness adjustment keys work out of the box but there are only 4 increments.

If I type in the following command as root:
```

# echo 1 > /sys/class/backlight/acpi_video0/brightness

```I get 8 increments, which I'm perfectly happy with, but the fix is only temporary.
Every time I reboot the increments go back to 4. How can I make this permanent? 
Or maybe is there another, better, solution to this problem?

Oh, yeah, I'm running Ubuntu 12.10

---

### Post by Aaron Christianson on 2012-11-19
There are a few ways.

If you are satisfied with the results of the command you are using, you can simply add the it to th bottom of the file '/etc/rc.local'
This is a script that is executed as root at boot, so the command should give the desired effect there. I haven't tested what you are trying, but it seems like it should work.

You can do this by hitting alt+F2 and typing 
```
gksu gedit /etc/rc.local
```and then adding the command and saving and closing.

other solutions:
There is a program you can download called xbacklight that will allow you to set it more precisely.

Install this program from the software center (may have to click on "show technical items.") or type in your terminal 

```
sudo apt-get install xbacklight 
```then you can open the keybinding application and create a new binding with a command. The command you want for getting brighter will be something like this

```
xbacklight + 12 
```You can rebind the brighter key to that.

```
xbacklight -12
```this will make it dimmer.

That will give you eight steps.

I use a special script so it moves by larger increments when it is brighter, and smaller when dimmer. (cuts by half each time until it is down to 1% backlight)
This is the script:

```
#!/bin/bash

# Just some functions with xbacklighter for keybindings.

level=$(($(xbacklight|cut -d "." -f1) + 1))

# cuts the backlight by half
half() { 
  [ $level -ge 99 ] && half=64 || half=$(( $level / 2 ))
  [ $half -eq 0 ] && half=1
  xbacklight -set $half
}

# doubles the backlight
dub() {
  dub=$(( $level * 2 ))
  xbacklight -set $dub
}

"$@"
```If you are interested in doing something a little more sophisticated like this, but are unsure what to do with this text, just ask.

---

### Post by goldfish777 on 2012-11-20
I lied.

 This the command that temporarily fixes my brightness:
```

echo -n 0 > /sys/module/video/parameters/brightness_switch_enabled

```

I stuck it in rc.local and rebooted. All is well. My brightness adjustments work to my satisfaction. 

Thank you very much.

---

