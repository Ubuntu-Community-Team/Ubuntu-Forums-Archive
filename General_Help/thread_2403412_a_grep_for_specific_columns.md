---
title: "a grep for specific columns"
date: 2018-10-11
forum: General Help
---

### Post by Skaperen on 2018-10-11
i have a large file (many millions of lines) that i need to do some column specific grepping on.  several of the patterns i need to search for i need to match only a specific white-space-separated column since other columns in other lines have matches but i don't want those lines to be matched.  lines should be considered a match if the pattern matches in a specified column.

has anyone seen such a program ... before i go write my own such program?

what i am thinking of is specifying one or more columns as options on the command line.

---

### Post by TheFu on 2018-10-11
If you need to do this once, I'd just egrep for the lines with the pattern, then pull the remaining lines into a spreadsheet and use autofilter on the column.

If I needed to do this more than once, I'd use a 5 line perl or awk script.  If the columns are quoted and the data isn't 100% guaranteed to be without white space, I'd use a CSV perl module to get the specific column for pattern matching.

If I didn't know perl, I'd work backwards using egrep to limit "suspected" lines with the needed text first, then awk or cut or sed to get the specific column and check for a match.

Scripts like these are commonly found on stackoverflow.
[https://stackoverflow.com/questions/43160845/awk-search-one-column-print-list-of-matches-in-second-column](https://stackoverflow.com/questions/43160845/awk-search-one-column-print-list-of-matches-in-second-column) is an example.

But again, if the columns could contain quoted values which might contain spaces, then I'd use perl with the CSV module.

---

### Post by Skaperen on 2018-10-13
that's the direction i ended up going although i used Python.  a decade ago i would have used C,

---

### Post by TheFu on 2018-10-13
If it is solved, please help the community by marking it **solved**.  Posting the solution so the next person can use it would be very helpful too.  Thread tools button near the top of this page.

---

