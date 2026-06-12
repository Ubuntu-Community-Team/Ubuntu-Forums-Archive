---
title: "indicator-datetime - I can not open the settings in Xubuntu 14.04"
date: 2014-12-15
forum: General Help
---

### Post by tellapu on 2014-12-15
I could install indicator-datetime in Xubuntu 14.04, but the Time & Date Settings would not open, perhaps because there is another "Time and Date" Settings in Xubuntu. In the dconf-editor I can edit most of the settings, but cannot enter a new city/time zone. My goal is to display multiple time zones displayed. Any help available?
Thanks!

---

### Post by ajgreeny on 2014-12-15
Install **xfce4-datetime-plugin** then add **DateTime** to your panel.

That is, I think, what you believe you my already have, but there are many other options to show time and date on the panel; none as good in my opinion.
You can then configure the **datetime** panel applet by right clicking it in the panel; it is much more configurable than the **orage-clock** or **clock** applets.

Not sure about multiple time zones being shown, however, so look at the alternatives as well.

---

### Post by tellapu on 2014-12-15
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747"), thanks a lot for your speedy note. I have not found yet any option for multiple time zones, I had installed before, and this is the crucial feature I want. But thanks anyway!

---

### Post by slickymaster on 2014-12-15
It's possible to display multiple timezones by using multiple applets of the Orage Clock Panel. Right click on the clock -> properties and in the clock dialog there is a button ('Time and Date Settings...') under the Timezone text-box. Clicking that button will bring up a dialog that allows you to select which timezone you want that applet to use. (You'll have to unlock this dialog by providing you password to edit it).

Each applet will use the timezone you set it for.

---

### Post by Elfy on 2014-12-15
You can sort of use Orage.

Middle click on orage in the panel and you'll get a new window Global Time - you can there set as many new timezones as you want.

Middle click to lose the global time window.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=258597&d=1418656403[/IMG]

---

### Post by tellapu on 2014-12-15
Wow, this is fast, great community! 
Thanks for the tips regarding Orage and the Global Time. In the meantime I found an answer to my specific question and have now several options how to get multiple time zones, wonderful! I will test them and will see which one I like the best.

Here is the answer to how to **set the different time zones in the indicator-datetime**:
[http://askubuntu.com/questions/155151/how-to-set-multiple-timezones-in-gnome-classic](http://askubuntu.com/questions/155151/how-to-set-multiple-timezones-in-gnome-classic)
**Dconf-editor**: Look at the *locations* field as shown and add your new location(s) - each entry is in the format ,'timezone city' i.e. separate entries with commas
Select com > canonical > indicator > datetime
  Look at the locations value.
  ['UTC UTC', 'Asia/Nicosia Nicosia']

---

