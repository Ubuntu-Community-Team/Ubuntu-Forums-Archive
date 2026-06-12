---
title: "cannot change the group mysqld runs as"
date: 2007-06-08
forum: General Help
---

### Post by xormar on 2007-06-08
Hi all

I've got a 6.06.1 LTS installation with mysql-server 5.0.22. I need to have mysqld run as a different user from the default one (mysql). So, I configured it in /etc/mysql/my.cnf:
[...]
user = ausername
group = agroupname
[...]

But when starting mysqld, I get a rather strange error:
# mysqld
Unknown suffix 'a' used for variable 'group_concat_max_len' (value 'agroupname')
070608 14:04:00 [ERROR] mysqld: Error while setting value 'agroupname' to 'group_concat_max_len'

And, VERY, strangely: The error seems to depend on the first letter of the group name. It does NOT appear if the group name starts with either one of g, k, or m, but with all others. And it occurs before the existence of the group is even checked (i.e. if the first letter is any other than g,k, or m, the error occurs independently of whether the group exists or not).

With g,k,m supposedly representing giga, kilo and mega, this seems to make sense in a way... but why would the value of "group" be used for calculating group_concat_max_len???

Does anybody have an idea what is going on?

thx /markus

---

### Post by kidders on 2007-06-09
Hi there,

Afaik there is no "group" directive. The configurator is possibly assuming you mean "group_concat_max_len", which expects a numeric argument (so common multiplier suffixes are being recognised). For instance, the default "group_concat_max_len" value is 1024, which could presumably be written as "1k".

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

