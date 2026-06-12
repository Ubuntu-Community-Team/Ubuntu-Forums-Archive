---
title: "[SOLVED] Firefox - turn off Work Offline permanently?"
date: 2008-07-06
forum: General Help
---

### Post by iloveannie on 2008-07-06
My computer dedicated to web development is never connected to the Internet, but it has apache running on it.  EVERY time I open Firefox 3 the 'Work Offline' option is checked and I need to uncheck it to view 127.0.0.1.  Is there a way to remove this obnoxious option so I'm always working online besides connecting my computer to the Internet?

Firefox 2 did not exhibit this behavior, and this 'feature' is a major regression in my mind.  

](*,)

---

### Post by Sealbhach on 2008-07-06
I believe Network Manager does that, but that's all I know.


.

---

### Post by Fingers &amp; Thumbs on 2008-07-06
> Firefox 2 did not exhibit this behavior, and this 'feature' is a major regression in my mind. 

+1

My regular connection is via a 3g usb modem, but I still use wireless when and where available. I have seen instructions to disable network manager so that FF3 will not switch to offline, but as I still use wireless when it's available, this method is of no use to me. Surely there is some way of making FF3 start in online mode.

Thus far, I have found none.

---

### Post by nanotube on 2008-07-07
see here:
[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=11503&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=11503&forumId=1)

and here:
[http://ubuntuforums.org/showthread.php?t=767045](http://ubuntuforums.org/showthread.php?t=767045) 

(summary: there's a bug filed with mozilla, and there's a workaround)

---

### Post by iloveannie on 2008-07-07
Thanks a million!
:D

And I was thinkin I had to switch to Internet Explorer...
:rolleyes:

---

### Post by nanotube on 2008-07-10
more FYI: this bug is supposedly going to be fixed in firefox 3.0.1 (the release candidate 1 of which was just posted today, and it will probably be released in another week or so). see more info in this list of bugs fixed for ff 3.0.1:

[https://bugzilla.mozilla.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Core&product=Firefox&product=Toolkit&long_desc_type=allwordssubstr&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=anywords&keywords=fixed1.9.0.1+verified1.9.0.1&emailtype1=substring&email1=&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=](https://bugzilla.mozilla.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Core&product=Firefox&product=Toolkit&long_desc_type=allwordssubstr&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=anywords&keywords=fixed1.9.0.1+verified1.9.0.1&emailtype1=substring&email1=&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=)

---

### Post by ghee22 on 2009-02-03
[https://addons.mozilla.org/en-US/firefox/addon/8502](https://addons.mozilla.org/en-US/firefox/addon/8502)

Extension to always be online

---

### Post by zansatsu0 on 2009-02-11
This is what worked for me, without having to install an addon. I found it here:
[http://fedoraforum.org/forum/showthread.php?t=200395]("http://fedoraforum.org/forum/showthread.php?t=200395")

Type the following in the address field:
```
about:config
```

In the filter field type:
```
networkmanager
```

Right click and select 'toggle' to set the following variable to true:
```
toolkit.networkmanager.disable
```

The problem is that Firefox is looking at NetworkManager to control the browsers online status. Since NetworkManager isn't always well-informed, especially in dial-up situations, this causes Firefox to think that no connection exists and forces Firefox to work offline. This, in-turn, leads to a case of user madness that leads to the smashing and breaking of keyboards unlike the world has ever seen. Well, in my case anyway. ](*,)

Just my $0.02.

---

### Post by lordamit on 2010-06-23
Thanks man :):biggrin: @zan

---

### Post by betlog on 2010-07-18
lol, and with knetworkmanager removed entirely (replaced it with wicd)  it evidently has problems :]

---

