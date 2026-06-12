---
title: "pdfpc package confusion"
date: 2017-09-07
forum: General Help
---

### Post by psionman on 2017-09-07
I am confused when trying to use the **pdfpc** package

[http://manpages.ubuntu.com/manpages/zesty/man1/pdfpc.1.html]("http://manpages.ubuntu.com/manpages/zesty/man1/pdfpc.1.html")

1. If I enter:

 ** pdfpc  PDF-file**

I get > command not found

 I have to use

**pdf_presenter_console**

2. If I enter 

pdf_presenter_console -h

I only get a restricted list of options compared to the man page:
> 
Pdf-Presenter-Console Version 2.0 Copyright 2009-2011 Jakob Westhoff
Usage:
  pdf_presenter_console [OPTION&#8230;] <pdf-file>

Help Options:
  -h, --help                    Show help options

Application Options:
  -d, --duration=N              Duration in minutes of the presentation used for timer display. (Default 45 minutes)
  -l, --last-minutes=N          Time in minutes, from which on the timer changes its color. (Default 5 minutes)
  -u, --current-size=N          Percentage of the presenter screen to be used for the current slide. (Default 60)
  -s, --switch-screens          Switch the presentation and the presenter screen.
  -c, --disable-cache           Disable caching and pre-rendering of slides to save memory at the cost of speed.
  -z, --disable-compression     Disable the compression of slide images to trade memory consumption for speed. (Avg. factor 30)

Can anyone please explain what's going on?

---

