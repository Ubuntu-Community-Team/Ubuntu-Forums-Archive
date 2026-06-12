---
title: "Simple MySQL question, I think"
date: 2020-05-26
forum: General Help
---

### Post by cscj01 on 2020-05-26
Can someone tell me what is wrong with the following MySQL code:```
mysql> alter table artist
    -> constraint foreign key (person_id)
    -> references person (person_id)
    -> on delete no action
    -> on update no action;
```
I get the following error when I execute it:```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'constraint foreign key (person_id)
references person (person_id)
on delete no ac' at line 2
```I know i did not name the foreign key, but according to the MySQL reference manual, MySQL will provide one for me.  I have done this before, but I seem to be losing my mind.

---

### Post by Holger_Gehrke on 2020-05-26
I think you're missing an 'add ' before 'constraint'. So it should read
```
alter table artist **add** foreign key (person_id) references person (person_id) on delete no action on update no action;
```
The 'constraint' is only needed if you want to give a name to this constraint; if you don't want to give it a name you can leave it out.

Holger

---

### Post by cscj01 on 2020-05-26
> **Holger_Gehrke said:**
> I think you're missing an 'add ' before 'constraint'. So it should read
```
alter table artist **add** foreign key (person_id) references person (person_id) on delete no action on update no action;
```
The 'constraint' is only needed if you want to give a name to this constraint; if you don't want to give it a name you can leave it out.

Holger

Thank you.  It's amazing how long I stared at that statement and never saw the missing **add**.  I suppose these old eyes need to go in for a tune-up.  That points out a good case for having someone else check your code.

---

