---
title: "vnstat not displaying any but the more recent information"
date: 2020-04-06
forum: General Help
---

### Post by col48 on 2020-04-06
**vnstat 1.14 under Ubuntu 16.04**

```
vnstat -i lo
```

returns only yesterday and today's usage (labelled 'yesterday' and 'today') and this month's (labelled - currently - Apr '20) on the given interface.  Without parameters it gives the same data but for each of the two available interfaces.

In neither case does it return any older information.  Why not?
I'm sure I used to see under daily every day in the current month and under monthly the 12 months up to and including the current one.

Furthermore, if I add any of the time parameters (-m, -d, -t, -w) it says there is no data available.

Do I need to add something to the config file, for instance?  I can't see any parameter which ought to influence this behaviour.

```
vnstat -i lo1 --dumpdb 
```
yields this right now (which suggests the data is really there):
```

version;3
active;1
interface;lo1
nick;
created;0
updated;1586183145
totalrx;152186
totaltx;20462
currx;71417412
curtx;3665528
totalrxk;961
totaltxk;787
btime;1586159114
d;0;1586127787;24;1;632;706;0
d;1;1586075375;414;16;906;276;0
d;2;1585954896;196;25;695;985;0
d;3;1585868437;1105;41;243;993;0
d;4;1585820584;626;25;715;427;0
d;5;1585695626;291;61;161;971;0
d;6;1585609202;318;17;842;204;0
d;7;1585561800;68;4;429;511;0
d;8;1585469676;385;17;226;399;0
d;9;1585394551;405;26;337;494;0
d;10;1585306527;1093;79;795;26;0
d;11;1585230371;72;3;578;982;0
d;12;1585094486;163;15;867;443;0
d;13;1585008064;230;60;860;64;0
d;14;1584960062;63;4;125;320;0
d;15;1584867651;495;16;437;650;0
d;16;1584780797;391;15;1002;667;0
d;17;1584662465;38;4;861;83;0
d;18;1584576246;207;8;469;169;0
d;19;1584489616;475;79;937;772;0
d;20;1584451214;501;23;142;914;0
d;21;1584348711;429;19;637;991;0
d;22;1584275550;861;29;793;604;0
d;23;1584144260;74;39;951;12;0
d;24;1584057671;309;11;41;189;0
d;25;1584016920;294;24;794;749;0
d;26;1583926783;12;1;561;114;0
d;27;1583832690;39;2;451;911;0
d;28;1583757618;255;9;517;128;0
d;29;1583625624;112;6;914;214;0
m;0;1585695626;2659;173;280;262;0
m;1;1583020941;8174;685;507;793;0
m;2;1580515494;7805;782;985;402;0
m;3;1577954885;4910;900;234;792;0
m;4;1575224335;4885;2002;906;313;0
m;5;1572620877;8757;1328;396;402;0
m;6;1569918796;8443;833;663;466;0
m;7;1567342152;12722;704;1;9;0
m;8;1564645675;10893;598;162;663;0
m;9;1561935703;9614;879;881;814;0
m;10;1559377404;6593;363;345;898;0
m;11;1556704256;7477;651;159;511;0
t;0;1543838940;89;2050;725;561;0
t;1;1568502032;1941;83;942;26;0
t;2;1542610890;1669;49;761;718;0
t;3;1563264547;1536;141;386;956;0
t;4;1568588457;1593;58;313;622;0
t;5;1565650853;1523;49;288;730;0
t;6;1575977664;366;1111;34;681;0
t;7;1561110473;1228;42;88;499;0
t;8;1566634574;1219;40;860;484;0
t;9;1551093210;1189;36;763;557;0
h;0;1586127787;14;6
h;1;0;0;0
h;2;0;0;0
h;3;0;0;0
h;4;0;0;0
h;5;0;0;0
h;6;0;0;0
h;7;0;0;0
h;8;1586159744;15904;449
h;9;1586163344;5291;410
h;10;1586166944;2;3
h;11;1586170544;2;3
h;12;1586174144;2;2
h;13;1586177744;1122;183
h;14;1586181345;2460;463
h;15;1586183145;425;217
h;16;1586102376;8;4
h;17;1586105976;2;3
h;18;1586109576;56550;1959
h;19;1586113177;154672;5822
h;20;1586116777;5;7
h;21;1586120377;126;41
h;22;1586123977;2;2
h;23;1586127577;13423;1321

```

This has been going on for a long time, as witness my old post

[https://ubuntuforums.org/showthread.php?t=2400039]("https://ubuntuforums.org/showthread.php?t=2400039")

The covid19 lockdown means there is more time to try to address these non-show-stopping questions....

---

