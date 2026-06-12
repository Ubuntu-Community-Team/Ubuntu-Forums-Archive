---
title: "LibreOffice"
date: 2013-02-16
forum: General Help
---

### Post by Crazy Bee on 2013-02-16
Hi :D
In Libreoffice calc : how to calculate the frequency of certain information in a column that meet certain criteria in another column for example :
how to calculate number of persons between age 10 and 20 that took 1 dose of a drug in the following table.
[IMG]http://www.m5zn.com/newuploads/2013/02/16/png//m5zn_496f79f738e567e.png[/IMG]

---

### Post by SteveDee on 2013-02-16
> **Crazy Bee said:**
> ...how to calculate number of persons between age 10 and 20 that took 1 dose of a drug in the following table...

Here is one way:-
In C2 type:-
=IF((A2>9)    AND    (A2<21)  AND  (B2=1),1,0)
Then replicate this in rest of C column (pull down the cross from lower right corner of C2 as far as row 12).
Then sum this column.

---

### Post by Crazy Bee on 2013-02-16
> **SteveDee said:**
> Here is one way:-
In C2 type:-
=IF((A2>9)    AND    (A2<21)  AND  (B2=1),1,0)
Then replicate this in rest of C column (pull down the cross from lower right corner of C2 as far as row 12).
Then sum this column.

:D  than you very much SteveDee it worked !!! \\:D/

---

