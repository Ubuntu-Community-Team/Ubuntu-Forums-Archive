---
title: "Firefox 52.0 won't accept session variables"
date: 2017-03-20
forum: General Help
---

### Post by Colin@oxford on 2017-03-20
I have a fairly simple website that has a form for users to fill in.  It uses session_id to communicate the fields filled in.  This worked fine in all browsers that I was aware of, but the latest change to firefox (to 52.0) seems to be preventing it from working.  The initial form (event_form.php) contains this:

<form id="event_form"
action="add_event.php" method="post" enctype="multipart/form-data">

and somewhere further down there is a "submit" button.  Pressing that button previously went to

 <my-website>/add_event.php?

but now it goes to:

<my-website>///event_form.php?PHPSESSID=mvvon6rqcivhdbvav92dnqold5

which does not show the correct information.

What do I need to set in my Firefox to get this working correctly again?  And why has it changed?

---

