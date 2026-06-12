---
title: "Date and Time data manipulation"
date: 2013-03-26
forum: General Help
---

### Post by ebodnaruk on 2013-03-26
Hi everyone,

I have a file that consists of a single column of temperature values.  I know the start date and the time step between entries.  Is there a nifty Unix-clever way to add a column (or multiple ones) to show the date and to be able to export selections of it?  

For instance, I have 20 years of temperature data at a 3 hr time step.  I have 20 * 365 * 8 data entries/rows.  Can I easily add some sort of time stamp to each of these?  Then, and most importantly, would there be an easy way to export all of the data just corresponding to a month like January across all the years?  

I'm fairly new to Linux/Unix systems and have seen a bit of the power of commands like awk and grep so I am just curious.  I could write up a brute force loop but am wondering if there's an elegent solution!  

Thanks so much!
Ethan

---

### Post by steeldriver on 2013-03-26
You could add a date / time stamp fairly easily by keeping a count of the row number and passing it to the 'date' function with a little bit of shell arithmetic e.g.

```

$ i=0; while read -r value; do echo $(date --date="31 Mar 1993 1pm + $((3*$i)) hours") "$value"; ((i++)); done < temps
Wed Mar 31 13:00:00 EST 1993 20.6
Wed Mar 31 16:00:00 EST 1993 21.0
Wed Mar 31 19:00:00 EST 1993 19.2
Wed Mar 31 22:00:00 EST 1993 17.8
Thu Apr 1 01:00:00 EST 1993 15.7
Thu Apr 1 04:00:00 EST 1993 13.0
Thu Apr 1 07:00:00 EST 1993 16.4
Thu Apr 1 10:00:00 EST 1993 17.1
Thu Apr 1 13:00:00 EST 1993 19.3
```

You could then select a particular month with awk e.g.

```
$ i=0; while read -r value; do echo $(date --date="31 Mar 1993 1pm + $((3*$i)) hours") "$value"; ((i++)); done < temps | awk '$2 ~ /Apr/ {print}'
Thu Apr 1 01:00:00 EST 1993 15.7
Thu Apr 1 04:00:00 EST 1993 13.0
Thu Apr 1 07:00:00 EST 1993 16.4
Thu Apr 1 10:00:00 EST 1993 17.1
Thu Apr 1 13:00:00 EST 1993 19.3
```

---

