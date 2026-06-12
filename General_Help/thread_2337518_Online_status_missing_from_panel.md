---
title: "Online status missing from panel"
date: 2016-09-19
forum: General Help
---

### Post by nenadcvetkovic on 2016-09-19
I've installed Ubuntu 16.04 (fresh install on new ssd). I wanted to save my time by copying the entire home folder from previous hard drive (still has working ubuntu 16.04) and exporting/importing program list in Synaptic. Everything is ok, the only thing that bugs me is that there are no Online status options in the panel. I have Empathy installed and I tried if installing Evolution will resolve the problem. Am I missing something?

---

### Post by ajgreeny on 2016-09-19
What do you see if you click on the fan icon to the left hand side of the **En** language icon?

That is the network applet icon so it shpould give you options to see the connection infpormation and tom edit the connection as well.

Or am I missing your point totally; it wouldn't be the first time I have done so?

---

### Post by nenadcvetkovic on 2016-09-19
I think you missed the point :) This menu should look similar to this (I found this pic somewhere on net). I'm missing statuses and Empathy menu item.

---

### Post by ajgreeny on 2016-09-19
Ah! Gotcha.

Sorry but in that case I do not have an answer; I don't use any applet to update anything except my emails, and I don't use an IM application any more.

---

### Post by nenadcvetkovic on 2016-09-20
Found a solution. In dconf editor, I set in com.canonical.indicator.messages applicaions ['thunderbird.desktop', 'empathy.desktop']. I only added empathy.desktop. Thunderbird appears here when I start Thunderbird :)

---

