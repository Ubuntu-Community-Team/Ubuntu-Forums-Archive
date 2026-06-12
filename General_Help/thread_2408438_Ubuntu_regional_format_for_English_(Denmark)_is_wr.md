---
title: "Ubuntu regional format for English (Denmark) is wrong"
date: 2018-12-18
forum: General Help
---

### Post by scporse on 2018-12-18
I really don't know where to post this so please bear with me (or move my post to another part of the ubuntu forums if you are a moderator).

I've discovered that the date format is wrong when choosing the preset English (Denmark) in Ubuntu Language support > Regional formats ([here]("https://postimg.cc/QFBJS4w7") is a screenshot of the place, I'm referring to) 

[IMG]https://postimg.cc/QFBJS4w7[/IMG]
It currently is YYYY-MM-DD but should instead be DD-MM-YYYY (source: I'm danish)
Generally speaking, the whole date string should be formatted similarly to that of: English (United Kingdom)

Can this be considered a bug and, in any case, where/how should it be reported?

---

### Post by deadflowr on 2018-12-18
*Thread moved to **General Help***

You can report bugs by following the reporting bugs wiki page here:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by scporse on 2018-12-20
Thanks, I found that web page also, but thought I should report my finding in some other way since I don't consider it a bug, but rather just a wrongful configuration of a regional setting / locale.
Anyway, I'll give it a try.

---

### Post by scporse on 2019-01-20
Since the thing I'm trying to report is not a bug per se, but rather a wrongful locale preset, I'm at a loss as to how I should report this?

I tried using "ubuntu-bug gnome-language-selector" via terminal, but this only results in the message: The problem cannot be reported. This report is about a package that is not installed.
The package, however, must be installed on my system, since i see a process with this very name, running when I open the language support application.

Any ideas how I should proceed here?

---

### Post by deadflowr on 2019-01-20
Are you sure it's not language-selector-gnome?
That exists and is the only package I see installed.

---

### Post by scporse on 2019-01-22
Nope: [IMG]https://postimg.cc/Z0HQVBCf[/IMG]

---

### Post by Skaperen on 2019-01-22
first, my background:  i have lived all my life in USA.  my internet nickname ("Skaperen" ... in English "The Creator") is based on my ancestry being part Norwegian and being creative in nature (*not* the NRK TV show of the same name).

it is my understanding that the only date formats with the '-' characters are established by [ISO 8601]("https://en.wikipedia.org/wiki/ISO_8601") (or it leaves that character out) which also establishes the _most-to-least-significant_ order of the numbers.  the order was originally established by [ISO 2014]("https://en.wikipedia.org/wiki/ISO_2014").  there could be formats i am not aware of, but my understanding of the format in UK/GB is that it uses '/' characters instead of '-' characters ... "DD/MM/YYYY" (like today is "22/1/2019" or "22/1/19").

some quick research on what is used in [Kongeriget Danmark]("https://en.wikipedia.org/wiki/Denmark") includes a few forms with '-' including one form standardized by [Dansk Sprognævn]("https://en.wikipedia.org/wiki/Dansk_Sprogn%C3%A6vn") (like "22/1-19").  the others are non-standard but perhaps in common use.  presumably this common use may include when the English language is use.  but is there any formal standard we can identify as "en_DK"?  i have never seen "en_DK".

researching UK/GB reveals British Standard has adopted ISO 8601 (as BS ISO 8601:2004) with "22/01/19" and "2019-01-22" being the commonly used forms.  i don't know if [Brexit]("https://en.wikipedia.org/wiki/Brexit") will change any of this.  if there are changes, i suspect it is more likely to just drop the "2019-01-22" rather than change the ordering.

in conclusion, i would say the date format of _YYYY-MM-DD_ *is correct* and that there is no bug for this issue (incorrect output format is considered a bug).

---

### Post by scporse on 2019-01-23
Well hello, then, fellow scandinavian :)

I must confess that I am uninformed when it comes to ISO standards, and thus I'm basing my statements solely on the fact that I am danish and have lived all my life in Denmark.
During my time in this nice, little country, I've never once used the date format of YYYY-MM-DD myself and neither have I ever been told that this is correct to to in a danish context.

In case we're unable to reach an agreement on this subject;
Would you happen to know if there is an easy and reliable/best-practice way to set a custom locale, based upon the English (Denmark) one - just with a DD-MM-YYYY date format?

---

