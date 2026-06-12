---
title: "Problem with Libre Office"
date: 2017-01-28
forum: General Help
---

### Post by nadrach on 2017-01-28
Today I opened a Libre Office template that includes Drop Caps on the first paragraph in a chapter, except that there were no Drop Caps.
Check back to other documents with Drop Caps used in them, all have disappeared.
Check Styles and Formatting and the Drop Caps box is unticked on the paragraph format.
This is on Libre Office 5.2.4-RC2 on Lubuntu 16.04.
Check other machines, including Lubuntu 14.04, same problem.
Except on one old slow machine running Lubuntu 14.04 that is not configured with the Libre Office PPA.  This is running Libre Office 4.2.8 (default for Lubuntu 14.04).  Drop Caps are back, as is the tick in the formatting box, therefore the flag for the tick box is being read out of the files ... all of them.
Just not on LO 5.2.4.
Check back my diary ... last time I used the particular document format was August 2016, on an earlier version of LO 5.
Tried to set the flag on a document, save it and read it back, using LO 5.2.4.  No go.  No flag read back from the file.
At some time in the last 6 months, an upgrade to LO 5.2 has disabled reading the Drop Caps flag on paragraph format from a Libre Office Writer file.
So I want to ask Libre Office ... Why, When and What for?
Problem is ... I can't find a simple forum or feedback facility for Libre Office to do this. They no longer run a forum. Jumping through hoops to create a Bugzilla/Wiki/etc. account for a simple feedback of a query has proven ... interesting ... and futile.
Does anyone know where I can post simple feedback to Libre Office, or have they just stopped wanting to know?

---

### Post by ian-weisser on 2017-01-28
Bugzilla is the right way to go, since you are not using a package from the Ubuntu repositories.

You have found a bug. They need to know. They need to see it. They need to know how to duplicate the problem to fix it.
That's not 'simple' feedback.

Despite the bureaucracy, it is _valued_ feedback.

---

### Post by nadrach on 2017-01-29
OK, finally got a login organised on AskLibreOffice ... third attempt, previous two ran foul of Captcha.
Further testing showed that up to LO 5.1.4 (default on 16.04) was OK for Drop Caps.
Question asked.

Thank you for the direct response.

---

### Post by nadrach on 2017-02-01
Bug found ... [https://bugs.documentfoundation.org/show_bug.cgi?id=101664](https://bugs.documentfoundation.org/show_bug.cgi?id=101664)
Fix is in the works.

---

### Post by ian-weisser on 2017-02-01
Hooray!

Looking through the bug, I see the efforts of no less than three fabulous contributors: The original reporter, the bisector, and the patch contributor. Community-driven software at it's best.

---

