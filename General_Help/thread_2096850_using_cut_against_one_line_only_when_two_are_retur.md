---
title: "using cut against one line only when two are returned"
date: 2012-12-21
forum: General Help
---

### Post by cbillson on 2012-12-21
I'm hoping this is possible, and as a scenario, its probably a good one :)

i have a log file, its formatted as two lines per event.

[INDENT]19/12-22:48:43.018  info [myprocess.processid.program]
    actual line of data output
[/INDENT]So, when i'm grep'ing for lines of events, i'm using *cat myfile | grep "actual line of data"* - but the data i need is on the line above so i'm using *cat myfile | grep -B1 "actual line of data"  *to return both lines.

Now i need to get some elements of the first line so i'm using cut - eg [I]var=$(cat myfile | grep -B1 "actual line of data" | cut -c1-2)

[/I]problem i have now is this makes $var equal to '19' and 'ac'

is there an equivalent to -B for cut - or a way of only passing the first line of the two to cut? ideally i use "actual line of data output" as my search, but only grab the line before, not both..

as always, thanks for all the assistance

Cheers
Chris

---

### Post by cbillson on 2012-12-21
> **cbillson said:**
> I'm hoping this is possible, and as a scenario, its probably a good one :)

i have a log file, its formatted as two lines per event.
[INDENT]19/12-22:48:43.018  info [myprocess.processid.program]
    actual line of data output
[/INDENT]So, when i'm grep'ing for lines of events, i'm using *cat myfile | grep "actual line of data"* - but the data i need is on the line above so i'm using *cat myfile | grep -B1 "actual line of data"  *to return both lines.

Now i need to get some elements of the first line so i'm using cut - eg [I]var=$(cat myfile | grep -B1 "actual line of data" | cut -c1-2)

[/I]problem i have now is this makes $var equal to '19' and 'ac'

is there an equivalent to -B for cut - or a way of only passing the first line of the two to cut? ideally i use "actual line of data output" as my search, but only grab the line before, not both..

as always, thanks for all the assistance

Cheers
Chris


sussed it, again possibly not the most elegant solution, but works :)

*var=$(cat myfile | grep -B1 "actual line of data" | grep -v "actual line of data" | cut -c1-2)*

---

