---
title: "Increse Number of Line Characters"
date: 2013-01-28
forum: General Help
---

### Post by borgward on 2013-01-28
How do I increase the number of characters in a line for Thunderbird 3.0.4?

I have it set at 60 right now. I need to increase so that I can display the full width of the results of smartctl with out it wrapping.

Hard to read!

Tom

---

### Post by ajgreeny on 2013-01-28
I see you have searched on the mozilla support site forum and got an answer for more up-to-date TB 17.  Is that also the case for your version, 3.0.4?

In case you are still a bit confused here is a screenshot showing the preferences boxes from TB 17, which may help you in tye right direction.

---

### Post by borgward on 2013-01-28
OK I found it. I see "This Might Void Your Warranty" "Changing ... can be harmful .... only continue if you are sure" Not sure! 

I found:
Preference Name....................Status...Type.....Value
mail.compose.wrap_to_window_width;.Default..boolean..false

Is that what I need to change? Change value to true?

Anyway to specify the number of characters per line?

---

### Post by ajgreeny on 2013-01-30
Yes, I think that's the setting you need to change to **true** by double clicking on it, which is how you toggle false/true.  It is not one of the values that would ever be likely to stop TB from working, so give it a try to see if it does what you want after restarting TB.

---

### Post by SeanBlader on 2013-01-30
> **borgward said:**
> OK I found it. I see "This Might Void Your Warranty" "Changing ... can be harmful .... only continue if you are sure" Not sure! 


I think more importantly is the question: how did you get a warranty on free software?

---

