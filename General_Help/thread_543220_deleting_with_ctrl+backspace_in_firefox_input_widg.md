---
title: "deleting with ctrl+backspace in firefox input widgets"
date: 2007-09-04
forum: General Help
---

### Post by alger on 2007-09-04
In windows, when using ctrl+backspace to delete text in a firefox text widget (including the url bar) it deletes text until it finds a non alfanumeric character, such as periods, commas, slashes...
In ubuntu it just stops when it finds a space. Is there any way to make it behave like firefox/windows? I've looked through about:config but no bells rang

Thank you

---

### Post by alger on 2007-09-05
As always, just a while after asking for a solution I found it myself:

[http://anti.teamidiot.de/nei/2006/10/firefox_punctuation_boundaries/](http://anti.teamidiot.de/nei/2006/10/firefox_punctuation_boundaries/)

Just for the record:

   1. Go to about:config
   2. Search for layout.word_select.stop_at_punctuation
   3. If it doesn’t exist, right-click and choose New > Boolean
   4. Set layout.word_select.stop_at_punctuation to true

---

