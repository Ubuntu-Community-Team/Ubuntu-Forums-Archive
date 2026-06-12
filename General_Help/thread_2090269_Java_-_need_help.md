---
title: "Java - need help"
date: 2012-12-01
forum: General Help
---

### Post by Cotopaxi on 2012-12-01
Hi all,

I am trying to start a german application, written under java called "Zettelkasten" (slipbox).

When I try to start is with

```
java -jar Zettelkasten.jar
```

I get the following error message:

> SEVERE: Application class de.danielluedecke.zettelkasten.ZettelkastenApp failed to launch
java.lang.NullPointerException
        at de.danielluedecke.zettelkasten.database.Bookmarks.getBookmarkPosition(Bookmarks.java:778)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateToolbarAndMenu(ZettelkastenView.java:2845)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateDisplay(ZettelkastenView.java:2613)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateAfterOpen(ZettelkastenView.java:10249)
        at de.danielluedecke.zettelkasten.ZettelkastenView.loadDocument(ZettelkastenView.java:8703)
        at de.danielluedecke.zettelkasten.ZettelkastenView.<init>(ZettelkastenView.java:635)
        at de.danielluedecke.zettelkasten.ZettelkastenApp.startup(ZettelkastenApp.java:131)
        at org.jdesktop.application.Application$1.run(Application.java:171)
        at java.awt.event.InvocationEvent.dispatch(Unknown Source)
        at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
        at java.awt.EventQueue.access$200(Unknown Source)
        at java.awt.EventQueue$3.run(Unknown Source)
        at java.awt.EventQueue$3.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
        at java.awt.EventQueue.dispatchEvent(Unknown Source)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.run(Unknown Source)

Exception in thread "AWT-EventQueue-0" java.lang.Error: Application class de.danielluedecke.zettelkasten.ZettelkastenApp failed to launch
        at org.jdesktop.application.Application$1.run(Application.java:177)
        at java.awt.event.InvocationEvent.dispatch(Unknown Source)
        at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
        at java.awt.EventQueue.access$200(Unknown Source)
        at java.awt.EventQueue$3.run(Unknown Source)
        at java.awt.EventQueue$3.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
        at java.awt.EventQueue.dispatchEvent(Unknown Source)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
        at java.awt.EventDispatchThread.run(Unknown Source)
Caused by: java.lang.NullPointerException
        at de.danielluedecke.zettelkasten.database.Bookmarks.getBookmarkPosition(Bookmarks.java:778)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateToolbarAndMenu(ZettelkastenView.java:2845)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateDisplay(ZettelkastenView.java:2613)
        at de.danielluedecke.zettelkasten.ZettelkastenView.updateAfterOpen(ZettelkastenView.java:10249)
        at de.danielluedecke.zettelkasten.ZettelkastenView.loadDocument(ZettelkastenView.java:8703)
        at de.danielluedecke.zettelkasten.ZettelkastenView.<init>(ZettelkastenView.java:635)
        at de.danielluedecke.zettelkasten.ZettelkastenApp.startup(ZettelkastenApp.java:131)
        at org.jdesktop.application.Application$1.run(Application.java:171)
        ... 14 more


Can anyone give me a helping hand?

Thanks!

---

### Post by Cotopaxi on 2012-12-02
It looks like this Ubuntuforum is not the place for Java problems.

Does anyone know a Java support forum?

Thanks again!:)

---

### Post by MutantJohn on 2012-12-02
Well, follow the code. It's telling you that there is a NullPointerException and I used to know Java before our class switched to C but I used to get that error all the time.

I do believe it comes from the variable (the pointer) not being initialized. So if you look at the method call, getBookmarkPosition, you'll see the variable it's attempting to use and I think if you follow that tree all the way down you'll find the code that initializes that variable.

It's either that or the variable is pointing at a Null value and you're trying to do something with nothing which as we all know is impossible.

I could be wrong but that's just my 2 cents. As always, take caution when listening to strangers on the internet.

---

### Post by QIII on 2012-12-02
Click the "Report Abuse" button and ask the staff to move the thread to the "Programming Talk" subforum.

The "Report Abuse" button can be used for constructive purposes, too.

Also, don't assume that just because you don't get an instant answer that you aren't going to get help here.  Remember that this is a volunteer forum, we help as we have time and we live all around the world.  The person with the perfect answer may live in Bangalore and the question may come from Des Moines.  There is quite a time zone difference and the guy in Bangalore also has a job, eats dinner and spends time with his kids.

Give it some time.  Bump if you don't hear back in 24 hours.  But don't bump sooner or everyone gets pushed down.

I'm sure you'll get help! :)

---

### Post by KdotJ on 2012-12-02
I would guess, by looking at that trace, that this is an issue with the application rather than with you. Maybe it requires other files with it to work? Such as a database of bookmarks perhaps?

---

### Post by Cotopaxi on 2012-12-07
First of all:

Thanks for all your replies and sorry for my late reply!

I have been travelling and just returned home.

Like QIII says: we live all around the globe and connect to this forum at different times.

QIII now one question: I am not able to find a "report abuse" procedure. Can you give me a helping hand?

Again thanks to all for your help! :popcorn:

---

