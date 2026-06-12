---
title: "Firefox3b5 lost its applications"
date: 2008-04-28
forum: General Help
---

### Post by michelux on 2008-04-28
Eversince the upgrade to FF3b5 I seem to have lost all applications in Firefox.
The application tab in preferences is empty. Even when I tell FF to use an application to open, for example a PDF file, the next time I restart FF the application is gone and the tab is empty again.

When I use FF2 all applications are there. I already tried to copy the profile of FF2 over the FF3 profile but still nothing.

Any ideas anybody, except keep using FF2? 8)

---

### Post by wankel on 2008-05-02
My application preferences are also empty on two systems after upgrading (didn't notice it on the testing system, since firefox is a bit heavy for it).

Some MIME/application settings seem to catch on after telling firefox once (for example, by browsing to /usr/bin/openoffice when the dialog pops up; firefox will complete the entry with ooffice or something).

It does not work every time though, and the application panel in the preferences does not get populated.


There are two more things:
- the back and forward buttons are gone, also from the Customize... dialog
- sessions are not kept, even though I switched it to "use homepage", restarted ff and set it back to "show tabs from last time".

Does anyone recognize those symptons? Does anyone know a solution or a hint in the right direction? I could not find other complaints than that from michelux, and others about java or flash.

Configuration:
- green cats theme and default theme
- quite a few extensions, half of them disabled by ff3b5.
- kubuntu 8.04 (kde3), one 32 and one 64 bit system

---

### Post by wankel on 2008-05-02
for those interested: one side-problem is solved :-)

session restore: I used to use tab mix plus session management. FF3 turned TMP off, but did not think of enabling the built-in session manager.

Looking for "session" in about:config showed some customizations, of which I turned the most straightforward ones back to default. 

Upon ff restart, I was presented with a session of -about- half a year ago :-P

---

### Post by wankel on 2008-05-02
Sorry for hyacking this thread.... Back/Forward buttons are back in place!

I'm used to moving all those buttons from the "Navigation" between the left border of FF and the "File" menu entry, and after that disabling the navigation bar alltogether.

FF3 turned out to pick this up as "Oh, back/forward is not appreciated", so the buttons were not even available for choosing in the customization-dialog. So far 33% of my problems are solved :-)


Hoping on a resolution on the applications though. Found out so far/guessing:
- ff uses the .mozilla/firefox/pluginreg.dat ; most applications that do pop up correctly, are named there
- maybe ff forwards MIME resolving to the OS?

If I come across an answer that's less ambiguous, I'll post again :-)

---

### Post by boomsb on 2008-06-26
I'm having the same issue, no applications listed in the preferences.

Scratch that, it appears as though there is a package called firefox-3.0-gnome-support.

---

