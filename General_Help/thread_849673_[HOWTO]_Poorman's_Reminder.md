---
title: "[HOWTO] Poorman's Reminder"
date: 2008-07-04
forum: General Help
---

### Post by diaa on 2008-07-04
**Poorman's Reminder**

 Do you forget to make tea/eggs after you have already started?
Do you forget to call your friend/parent again after 10 minutes(because he was busy)?
It happens to all of us, I kept searching for the perfect reminding program for this but then I noticed it doesn't need a program on its own, you can accomplish this using a couple of simple bash commands.
Ok, now I'm making tea and I don't want to forget it, it should take 5 minutes, all I want to remember is a special beep.
Type the following in a terminal window:
```
sleep 300;beep -l 2000
```What's 300? it's the number of seconds to wait, 5 minutes * 60 seconds per minute = 300 seconds, ok what's 2000? it's the length of the beep in milliseconds(one second is 1000 milliseconds), so 2000 is 2 seconds, which is a noticeably long beep so you can notice, that's all, isn't it nice?

If you don't like the beep and you want a friendly message box with a meaningful message, don't worry, use the following command instead:
```
sleep 300;zenity --info --text="Time for making the tea"
```[I]
Note: This requires that you have zenity installed[/I]

If you don't like doing math, don't worry too
```
sleep $((60*60*2));beep -l 2000
```This beeps after 2 hours.

*Note: You can also mix and match, you can have both the beep and the message box*

If you use yakuake or tilda or something similar, this gets very convenient as it doesn't require a new window(which just clutters the taskbar), if you don't use them and you don't want to keep a terminal window open for this? No problem, use the following command
```
 screen bash -c "sleep 5;beep -l 4000"
```then close the terminal window and it'll continue running in the background :)

I've also wrote a small helper script to make this easier, It's called beepafter, you can find it attached, it can be run like this
```

beepafter.sh 5m
beepafter.sh 1h
beepafter.sh 1.5h

```Note that *beep* is not a standard package and needs to be installed manually, one possible way is
```
sudo apt-get install beep
```UPDATE: Added beepafter script

[SIZE=3][B][I]If you prefer a GUI reminder, I suggest trying [the open-source, cross-platform CookTimer]("http://cooktimer.googlecode.com/")

[/I][/B][/SIZE]

---

### Post by manfer on 2008-07-04
Maybe you'd like this one too:

prompt:~$ **sleep 300; espeak "Time for making the tea"; beep -f 1100 -r 10 -l 200**

---

### Post by Butthead on 2008-07-04
Or, if (lazy, like me :) ) and using the KDE desktop, just install "KTeaTime" from the repros. :guitar:

---

### Post by Herman on 2008-07-04
I agree with what the other people have already posted.

I would like to add that we can also easily have a picture pop up, (perhaps a picture of a tea pot or something), at the same time as we have espeak reminding us '**"Time for making the tea". **
I recommend installing gthumb picture viewer and optionally, openclip art for that, (you can use your own image files instead if you prefer).
```
sudo apt-get install gthumb openclipart
```So, the command would be:
```
sleep 300; espeak "Time for making the tea"; beep -f 1100 -r 10 -l 200 ; gthumb /usr/share/openclipart/png/food/beverages/teapot_ganson.png
```:lolflag:
> Or, if (lazy, like me :) ) and using the KDE desktop, just install "KTeaTime" from the repros. :) Yes, and if you use Gnome you can configure calendar appointments in Evolution similarly. 
Here's a link about how to do that, [Memos, Tasks and Calendar Appointments]("http://users.bigpond.net.au/hermanzone/p5.htm#Memos_Tasks_and_Calendar_Appointments"). :)

Regards, Herman

---

### Post by starcannon on 2008-07-04
when using espeak, be sure to use commas creatively to make it more understandable, a few ebonics tricks can sometimes be useful as well.

---

