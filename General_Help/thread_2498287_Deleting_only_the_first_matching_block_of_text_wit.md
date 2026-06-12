---
title: "Deleting only the first matching block of text with sed"
date: 2024-06-07
forum: General Help
---

### Post by vanadium on 2024-06-07
I am looking to delete old events from a calendar file, *.ics. The structure of such file is as:

```

BEGIN:VCALENDAR
 ...
BEGIN:VEVENT
 ...
END:VEVENT
BEGIN:VEVENT
 ...
END:VEVENT
END:VCALENDAR

```


In a script, I would want to 1) retrieve the first event, 2) check its age and 3) delete that event depending on its age. Retrieving the first event in the file is possible with

> 
sed -n '/BEGIN:VEVENT/,/END:VEVENT/p; /END:VEVENT/q' test.ics 


However, I do not find how I can delete only that first event:

> 
sed  '/BEGIN:VEVENT/,/END:VEVENT/d' test.ics 


is "greedy", i.e., will delete all events, from the first occurrence of BEGIN:VEVENT to the very last occurrence of END:VEVENT.

Attempting 

> 
sed  '/BEGIN:VEVENT/,/END:VEVENT/d ; /END:VEVENT/q' test.ics 


makes no difference.

Is it possible to have sed delete only the first block of matching text?

---

### Post by ActionParsnip on 2024-06-07
What does the date line of the event look like please?

---

### Post by currentshaft on 2024-06-07
Do you need to use sed? This is much easier and efficient to accomplish in a scripting language like Python.

---

### Post by #&amp;thj^% on 2024-06-07
currentshaft has a good choice with Python, 

@ vanadium, would this be something as a starting point: [https://gist.github.com/pboesch/7846aed47914adc7f34c527fceb8d200](https://gist.github.com/pboesch/7846aed47914adc7f34c527fceb8d200)

You would have to add/change your preferences to the script.

---

### Post by vanadium on 2024-06-08
Thank you for the feedback. Indeed, it does not need to be "sed", but I am baffled that what I was looking for is not possible with sed. While it is possible to printing only a single block, it appears deleting it is not. 

@1fallen, thank you for locating the script which indeed does what I was looking for. I didn't find one myself. In the mean time, I also cobbled a bash script together that just parses the file line by line and copies every line over to the output, except when an event starts. Then, the event is saved to a separate file, the date is determined and the event is only added to the output if it is not "old".

Thanks for all input. I am not yet proficient in Python, unfortunately.

---

