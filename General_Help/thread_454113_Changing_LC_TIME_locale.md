---
title: "Changing LC_TIME locale"
date: 2007-05-25
forum: General Help
---

### Post by Jeroen1000 on 2007-05-25
Hello to all,


I would like to change LC_TIME in order to change the way dates are displayed. Now ubuntu displays the month name as text and I would like it to display it as a number. At the bottom of my post is a list of variables that can be changed (type locale -k LC_TIME at the command prompt to get this list).

I'm particularly interested in this line: date_fmt="%a %b %e %H:%M:%S %Z %Y". 

Does anyone know how to change this?

Many thanks,

JEroen




abday="zo;ma;di;wo;do;vr;za"
day="zondag;maandag;dinsdag;woensdag;donderdag;vrijdag;zaterdag"
abmon="jan;feb;mrt;apr;mei;jun;jul;aug;sep;okt;nov;dec"
mon="januari;februari;maart;april;mei;juni;juli;augustus;september;oktober;november;december"
am_pm=";"
d_t_fmt="%a %d %b %Y %T %Z"
d_fmt="%d-%m-%y"
t_fmt="%T"
t_fmt_ampm=""
era=
era_year=""
era_d_fmt=""
alt_digits=
era_d_t_fmt=""
era_t_fmt=""
time-era-num-entries=0
time-era-entries="z"
week-ndays=7
week-1stday=19971130
week-1stweek=0
first_weekday=2
first_workday=1
cal_direction=1
timezone=""
date_fmt="%a %b %e %H:%M:%S %Z %Y"
time-codeset="UTF-8"

---

### Post by fanatik on 2007-05-25
look here for some info:

[http://gentoo-wiki.com/HOWTO_localedef]("http://gentoo-wiki.com/HOWTO_localedef")

you need to use localedef to change your settings.

---

