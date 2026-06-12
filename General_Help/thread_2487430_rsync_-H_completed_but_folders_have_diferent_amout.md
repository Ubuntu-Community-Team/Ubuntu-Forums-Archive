---
title: "rsync -H completed but folders have diferent amout of data in them"
date: 2023-06-04
forum: General Help
---

### Post by funkytwig4 on 2023-06-04
I did the following

[COLOR=#000000][FONT=Courier New]rsync -azv -H --delete root@192.168.1.55:/data/ /data

[FONT=arial]To sync 2 servers, whitch completed fine.  There is nothing being changed in this filesystem.

Ihen did the folowing on goth of them to do a quick check

[FONT=courier new]sudo du -hc --max-depth=1 /data/sun/backup/[/FONT]

But the results were different.  The total amount of data is the same but it is in doferent places

Source server

[/FONT][/FONT][/COLOR][COLOR=#008000][FONT=&amp][FONT=arial]754G    /data/sun/backup/sun_oc_1617219901_M_Wed_31Mar2021_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
267G    /data/sun/backup/sun_oc_1638305101_M_Tue_30Nov2021_2045
158G    /data/sun/backup/sun_oc_1648755902_M_Thu_31Mar2022_2045
87G     /data/sun/backup/sun_oc_1559331901_Y_Fri_31May2019_2045
7.7G    /data/sun/backup/sun_oc_1651347901_M_Sat_30Apr2022_2045
[/FONT][/FONT][/COLOR][COLOR=#0000ff][FONT=&amp][FONT=arial]26G     /data/sun/backup/sun_oc_1659443401_M_Tue_02Aug2022_1330[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
4.6G    /data/sun/backup/sun_oc_1624218301_M_Sun_20Jun2021_2045
35G     /data/sun/backup/sun_oc_1640983501_M_Fri_31Dec2021_2045
3.7G    /data/sun/backup/sun_oc_1656618301_M_Thu_30Jun2022_2045
[/FONT][/FONT][/COLOR][COLOR=#800080][FONT=&amp][FONT=arial]3.3G    /data/sun/backup/sun_oc_1654026301_M_Tue_31May2022_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
2.6G    /data/sun/backup/sun_oc_1659296701_M_Sun_31Jul2022_2045
6.6G    /data/sun/backup/sun_oc_1619811901_M_Fri_30Apr2021_2045
1.8G    /data/sun/backup/sun_oc_1622490301_M_Mon_31May2021_2045
169M    /data/sun/backup/sun_oc_1659444301_Y_Tue_02Aug2022_1345
[/FONT][/FONT][/COLOR][COLOR=#ff0000][FONT=&amp][FONT=arial]5.4G    /data/sun/backup/sun_oc_1635713101_M_Sun_31Oct2021_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
3.4G    /data/sun/backup/sun_oc_1643661901_M_Mon_31Jan2022_2045
9.3G    /data/sun/backup/sun_oc_1646081101_M_Mon_28Feb2022_2045
13G     /data/sun/backup/sun_oc_1606769101_Y_Mon_30Nov2020_2045
1.4T    /data/sun/backup/
**1.4T    total**

Target Server

[/FONT][/FONT][/COLOR][COLOR=#ff0000][FONT=&amp][FONT=arial]938G    /data/sun/backup/sun_oc_1635713101_M_Sun_31Oct2021_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
43G     /data/sun/backup/sun_oc_1622490301_M_Mon_31May2021_2045
[/FONT][/FONT][/COLOR][COLOR=#800080][FONT=&amp][FONT=arial]91G     /data/sun/backup/sun_oc_1559331901_Y_Fri_31May2019_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
87G     /data/sun/backup/sun_oc_1640983501_M_Fri_31Dec2021_2045
152G    /data/sun/backup/sun_oc_1659443401_M_Tue_02Aug2022_1330
[/FONT][/FONT][/COLOR][COLOR=#008000][FONT=&amp][FONT=arial]4.0G    /data/sun/backup/sun_oc_1648755902_M_Thu_31Mar2022_2045[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
2.6G    /data/sun/backup/sun_oc_1659296701_M_Sun_31Jul2022_2045
19G     /data/sun/backup/sun_oc_1606769101_Y_Mon_30Nov2020_2045
[/FONT][/FONT][/COLOR][COLOR=#0000ff][FONT=&amp][FONT=arial]169M    /data/sun/backup/sun_oc_1659444301_Y_Tue_02Aug2022_1345[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Courier New][FONT=arial]
3.4G    /data/sun/backup/sun_oc_1643661901_M_Mon_31Jan2022_2045
9.4G    /data/sun/backup/sun_oc_1638305101_M_Tue_30Nov2021_2045
3.6G    /data/sun/backup/sun_oc_1654026301_M_Tue_31May2022_2045
2.1G    /data/sun/backup/sun_oc_1624218301_M_Sun_20Jun2021_2045
9.6G    /data/sun/backup/sun_oc_1617219901_M_Wed_31Mar2021_2045
9.3G    /data/sun/backup/sun_oc_1646081101_M_Mon_28Feb2022_2045
3.5G    /data/sun/backup/sun_oc_1656618301_M_Thu_30Jun2022_2045
6.6G    /data/sun/backup/sun_oc_1619811901_M_Fri_30Apr2021_2045
3.4G    /data/sun/backup/sun_oc_1651347901_M_Sat_30Apr2022_2045
1.4T    /data/sun/backup/
**1.4T    total**

I realise the folders are in a diferent order but I have colour coded some to help.

What is going on, should I be worried?

Ben





[/FONT]
[/FONT][/COLOR]

---

### Post by funkytwig4 on 2023-06-04
OK, if I do -hcl I get same result on both sides

203G    /data/sun/backup/sun_oc_1559331901_Y_Fri_31May2019_2045
707G    /data/sun/backup/sun_oc_1606769101_Y_Mon_30Nov2020_2045
754G    /data/sun/backup/sun_oc_1617219901_M_Wed_31Mar2021_2045
780G    /data/sun/backup/sun_oc_1619811901_M_Fri_30Apr2021_2045
778G    /data/sun/backup/sun_oc_1622490301_M_Mon_31May2021_2045
786G    /data/sun/backup/sun_oc_1624218301_M_Sun_20Jun2021_2045
938G    /data/sun/backup/sun_oc_1635713101_M_Sun_31Oct2021_2045
959G    /data/sun/backup/sun_oc_1638305101_M_Tue_30Nov2021_2045
1014G   /data/sun/backup/sun_oc_1640983501_M_Fri_31Dec2021_2045
1019G   /data/sun/backup/sun_oc_1643661901_M_Mon_31Jan2022_2045
1.1T    /data/sun/backup/sun_oc_1646081101_M_Mon_28Feb2022_2045
1.1T    /data/sun/backup/sun_oc_1648755902_M_Thu_31Mar2022_2045
1.1T    /data/sun/backup/sun_oc_1651347901_M_Sat_30Apr2022_2045
1.1T    /data/sun/backup/sun_oc_1654026301_M_Tue_31May2022_2045
1.1T    /data/sun/backup/sun_oc_1656618301_M_Thu_30Jun2022_2045
1.1T    /data/sun/backup/sun_oc_1659296701_M_Sun_31Jul2022_2045
1.1T    /data/sun/backup/sun_oc_1659443401_M_Tue_02Aug2022_1330
1.1T    /data/sun/backup/sun_oc_1659444301_Y_Tue_02Aug2022_1345
16T     total

so it looks OK

---

### Post by funkytwig4 on 2023-06-04
OK, if I do -hcl I get same result on both sides

203G    /data/sun/backup/sun_oc_1559331901_Y_Fri_31May2019_2045
707G    /data/sun/backup/sun_oc_1606769101_Y_Mon_30Nov2020_2045
754G    /data/sun/backup/sun_oc_1617219901_M_Wed_31Mar2021_2045
780G    /data/sun/backup/sun_oc_1619811901_M_Fri_30Apr2021_2045
778G    /data/sun/backup/sun_oc_1622490301_M_Mon_31May2021_2045
786G    /data/sun/backup/sun_oc_1624218301_M_Sun_20Jun2021_2045
938G    /data/sun/backup/sun_oc_1635713101_M_Sun_31Oct2021_2045
959G    /data/sun/backup/sun_oc_1638305101_M_Tue_30Nov2021_2045
1014G   /data/sun/backup/sun_oc_1640983501_M_Fri_31Dec2021_2045
1019G   /data/sun/backup/sun_oc_1643661901_M_Mon_31Jan2022_2045
1.1T    /data/sun/backup/sun_oc_1646081101_M_Mon_28Feb2022_2045
1.1T    /data/sun/backup/sun_oc_1648755902_M_Thu_31Mar2022_2045
1.1T    /data/sun/backup/sun_oc_1651347901_M_Sat_30Apr2022_2045
1.1T    /data/sun/backup/sun_oc_1654026301_M_Tue_31May2022_2045
1.1T    /data/sun/backup/sun_oc_1656618301_M_Thu_30Jun2022_2045
1.1T    /data/sun/backup/sun_oc_1659296701_M_Sun_31Jul2022_2045
1.1T    /data/sun/backup/sun_oc_1659443401_M_Tue_02Aug2022_1330
1.1T    /data/sun/backup/sun_oc_1659444301_Y_Tue_02Aug2022_1345
16T     total

so it looks OK but ime curious?

---

### Post by aljames2 on 2023-06-04
Using the H option with rsync preserves hard links in your source.  This likely is throwing off your comparison using a normal du command.  You added -l option to also count links.

Read more about rsync -H option at:  man rsync

I recommend any time you run rsync with —delete, that you also include —dry-run.  This will simulate the completion of the command so you can see what will happen, to make sure bad things are not going to happen in case you’re half asleep when you run your next rsync.  If all looks good to you, then remove the —dry-run option to make it for real.

---

