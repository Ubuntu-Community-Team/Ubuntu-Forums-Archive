---
title: "ksysguard wildcard syntax"
date: 2014-08-29
forum: General Help
---

### Post by betlog-hax on 2014-08-29
I'm trying to make a drive I/O monitoring tab for ksysguard.
I have quite a few drives, and about half of them are often not attached. Plus I would like to graph *ALL* of them all the time.
So I figured i'd use a wildcard to make a single graph of total read and writes... but I can't figure out how to do it with wildcards.
Yes I know I can drag every drive in, but that's not what I'm asking.

I want something like:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE KSysGuardWorkSheet>
<WorkSheet title="Drive I/O" interval="0.5" locked="0" rows="2" columns="1">
 <host port="-1" command="ksysguardd" shell="" name="localhost"/>
 <display title="Read I/O" version="1" row="0" class="FancyPlotter" hScale="2" unit="" showUnit="0" column="0" autoRange="1" hLines="1" manualRange="0" vScroll="0" svgBackground="widgets/plot-background" vLines="0" vDistance="30" stacked="0" labels="1">
  <beam sensorName="disk/sd.*_\(.*:.*.*\)/Rate/rblk" sensorType="float" hostName="localhost" color="0xff004000"/>
 </display>
 <display title="Write I/O" version="1" row="1" class="FancyPlotter" hScale="2" unit="" showUnit="0" column="0" autoRange="1" hLines="1" manualRange="0" vScroll="0" svgBackground="" vLines="0" vDistance="30" stacked="0" labels="1">
  <beam sensorName="disk/sd.*_\(.*:.*.*\)/Rate/wblk" sensorType="float" hostName="localhost" color="0xff400000"/>
 </display>
</WorkSheet>

```

Suggestions?

---

