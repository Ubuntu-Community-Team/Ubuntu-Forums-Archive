---
title: "Time opening of Seamonkey"
date: 2018-07-12
forum: General Help
---

### Post by raleigh3 on 2018-07-12
I am trying to time how long it takes to open some browsers.

Not working.

```
time seamonkey
ReminderFox  clh(1)  {rmFx_cmdLine: [xpconnect wrapped nsICommandLine]}
```

---

### Post by &amp;KyT$0P# on 2018-07-12
Does [this addon]("https://addons.mozilla.org/seamonkey/addon/about-startup/") do what you want?

---

### Post by TheFu on 2018-07-12
Stopwatch?

The **time** command times a running process to completion.  So you'd need to start the browser, render the page and immediately close the application to get anywhere near a time for comparison.  All of those will have different times due to things outside your control.  Running the test 100 times might provide an average.

You can also use a programming tool called a profiler, but this requires advanced programming skills.

I would expect addons for the main  browsers to include some sort of tools to measure page loading times and times for the individual components.  [https://developer.mozilla.org/en-US/docs/Tools/Performance](https://developer.mozilla.org/en-US/docs/Tools/Performance) for example.

---

### Post by raleigh3 on 2018-07-17
> **halogen2 said:**
> Does [this addon]("https://addons.mozilla.org/seamonkey/addon/about-startup/") do what you want?

Thanks. I could not figure out how it works.

---

### Post by raleigh3 on 2018-07-17
> **TheFu said:**
> Stopwatch?

The **time** command times a running process to completion.  So you'd need to start the browser, render the page and immediately close the application to get anywhere near a time for comparison.  All of those will have different times due to things outside your control.  Running the test 100 times might provide an average.

You can also use a programming tool called a profiler, but this requires advanced programming skills.

I would expect addons for the main  browsers to include some sort of tools to measure page loading times and times for the individual components.  [https://developer.mozilla.org/en-US/docs/Tools/Performance](https://developer.mozilla.org/en-US/docs/Tools/Performance) for example.

I tried to post an answer but I got this message.

You don't have permission to access /newreply.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by &amp;KyT$0P# on 2018-07-17
> **raleigh3 said:**
> Thanks. I could not figure out how it works.
Just go to [FONT=Courier New]about:startup[/FONT]

---

### Post by raleigh3 on 2018-07-17
Thanks.

I found this. 

[https://askubuntu.com/questions/1054649/time-how-long-to-open-seamonkey?noredirect=1#comment1724550_1054649](https://askubuntu.com/questions/1054649/time-how-long-to-open-seamonkey?noredirect=1#comment1724550_1054649)

Much easier to use and understand.

---

