---
title: "webcal and calenders"
date: 2014-12-06
forum: General Help
---

### Post by andrew_s4 on 2014-12-06
I've just been sent a link to a calender from work, that when clicked on, on my ipad sets itself up on my ipad calender just fine. But when using firefox and Ubuntu 14.04 and click on the link from my outlook.com account to install itself to my outlook.com calender nothing happens. I'm not sure where the problem lies. As I said I'm using firefox and online outllook.com mail server and ubuntu 14.04 only. The link comes from my employer's icloud. 

When I post the link directly into firefox a popup tells me I have associate the link with a program. The link starts off like this  
webcal://p17-calendars.icloud.com/published.... 

Any ideas as to where the problem is?

---

### Post by TheFu on 2014-12-07
I use Thunderbird and Lightning for calendaring - not to outlook.com, but to a Zimbra server with multiple userids.  Wouldn't know how to get firefox to handle a .ics file, but Lightning can.

---

### Post by amanchesterman on 2014-12-07
If you have Thunderbird with the Lightning calendar, then if you go to File > New > Calendar and choose 'on the network', you can specify that the file is in ICS format and you can enter the web address. I've never done it myself but it looks like it should work!

---

### Post by TheFu on 2014-12-07
> **amanchesterman said:**
> If you have Thunderbird with the Lightning calendar, then if you go to File > New > Calendar and choose 'on the network', you can specify that the file is in ICS format and you can enter the web address. I've never done it myself but it looks like it should work!

Yes, this is correct.  The addresses are like this:
  [https://mail.example.com/dav/thefu@example.com/Calendar](https://mail.example.com/dav/thefu@example.com/Calendar)
But this is Zimbra specific. Don't know how outlook.com does it - MSFT tends to extend standards to the point they don't follow the standard anymore. Anyway, there should be clear documentation for the URL used by Outlook.com.

It still may be possible to get firefox to do this - I just don't know how or if it is even possible.

---

