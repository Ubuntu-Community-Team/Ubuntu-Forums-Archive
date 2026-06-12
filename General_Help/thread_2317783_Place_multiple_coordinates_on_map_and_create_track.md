---
title: "Place multiple coordinates on map and create track"
date: 2016-03-19
forum: General Help
---

### Post by chris137 on 2016-03-19
Hi,
I don't think I'm in the right place with it but I wasn't sure where else to put it. General Help seems to hit it.

I am generating a few hundred coordinates including timestamps per day which I'd like to display on a map.
Important factor: This must be possible via the commandline and completely automatic:
Let's say this script runs every day at 00:01 to read the previous day's coordinate-set which may be formatted in any way needed. It should output a map - not neccessarily interactive, might be just a picture - of a track displaying all these coordinates.
This would then be uploaded to a webserver where it is accessed as map, picture or whatever.
It would also be great if the timestamp could be displayed, maybe by a mouseover but I guess that's already a bit over the top.

Do any of you know a solution for this?
It is very important that it's a commandline tool and may be used with a cronjob or similar.

Possibly there are other suggestions on how to visualize a large set of coordinates.
Maybe important to add: This is about a motion profile so many of the given coordinates are very close together.


Thanks

---

### Post by dragonfly41 on 2016-03-19
Reading your requirement these are the key components I would search for via google

D3.js .. a visualisation framework which takes json input

streaming json .. so that you can add items incrementally to a large json file

e.g.
[https://www.npmjs.com/package/stream-json](https://www.npmjs.com/package/stream-json)

python .. so that you can run python parsing script from command line and cron.

...

There are other visualisation frameworks to explore .. for example raphael.js

[http://www.bryanbraun.com/2014/11/09/how-to-make-maps-with-raphaeljs](http://www.bryanbraun.com/2014/11/09/how-to-make-maps-with-raphaeljs)

But these are just rough ideas.

The important point is generating the growing json file incrementally via command line.

---

### Post by chris137 on 2016-03-20
To be honest this doesn't get my anywhere.
Everything I understand about it seems right, which is: map and writing stuff to a file. I don't really get more of it.

Right now I just put these coordinates in a text file.
I'm a bash person and never worked with json.
Also I'm not really sure how I'd get dots on a map using your solution.
Must be a little more detailed for me :P

---

### Post by jim_deadlock on 2016-03-20
What you're looking for is GPX format. This is a file which can be opened by most tracker software including Google Earth. You could upload your GPX files (.gpx extension) and then people could open them in Google Earth (or any other GPS software they have).

The GPX format is actually quite simple, if you know a bit of scripting you could easily build the files yourself. You don't mention how you've amassed your coordinates, but chances are whatever device/software you're using, it probably has a GPX conversion option. Example of GPX format below.

```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<trk>
<name>chris137 Track Sample</name>
<desc>Color:004000ff</desc>
<trkseg>
<trkpt lat="51.570068" lon="0.055919">
<ele>107.449997</ele>
<time>2015-06-20T13:30:31Z</time>
<speed>0.68</speed>
</trkpt>
<trkpt lat="51.570004" lon="0.055909">
<ele>107.439995</ele>
<time>2015-06-20T13:30:35Z</time>
<speed>0.00</speed>
</trkpt>
</trkseg>
</trk>
</gpx>
```

---

### Post by chris137 on 2016-03-20
Not quite what I was looking for.
It's actually a key requirement that this map is automatically created and may be viewed via a browser.
However if this won't work gpx is what I had an eye on already for manually viewing the track in Google Earth.

---

### Post by dragonfly41 on 2016-03-20
> 
Right now I just put these coordinates in a text file.
I'm a bash person and never worked with json.
Also I'm not really sure how I'd get dots on a map using your solution.
Must be a little more detailed for m


I can't help much more if you don't understand json or don't have take the time to research how to apply. You don't explain what "map" you are trying to render. Is it a geographic map?

You just need to have a converter to run in a bash script to convert  (say) a *.csv file containing your x,y,timestamp coordinates to *.json file which is required by visualisation frameworks.

That can't be too difficult if you understand bash scripting.

Searching around I found this blog ...

[http://blog.secaserver.com/2013/12/convert-csv-json-bash/](http://blog.secaserver.com/2013/12/convert-csv-json-bash/)


And the reverse JSON to CSV (if you need it) ...

[https://github.com/archan937/jsonv.sh](https://github.com/archan937/jsonv.sh)



Given that you now have your coordinates in json format you can post to a remote server which will have raphael.js installed and a cron job to refresh page for each update of json input.

Focussing on raphael.js (but as I wrote there are many other visualisation frameworks such as D3.js) you can learn from examples such as here ...

[http://dmitrybaranovskiy.github.io/raphael/](http://dmitrybaranovskiy.github.io/raphael/)

[http://jsfiddle.net/neveldo/xd2azoxL/](http://jsfiddle.net/neveldo/xd2azoxL/)

[http://www.vincentbroute.fr/mapael/](http://www.vincentbroute.fr/mapael/)

[https://parall.ax/blog/view/2985/tutorial-creating-an-interactive-svg-map](https://parall.ax/blog/view/2985/tutorial-creating-an-interactive-svg-map)

....

You might also meet your requirements by researching google maps.

---

### Post by chris137 on 2016-03-29
Just a little update so you know your post is appreciated:
I was hoping for an easier solution since your proposol kinda cracks the scope of this project.
Your answer is noted and I will deal with this when I have more time to invest in this project.

In the mean time other solution are still welcome (both solutions which take time to read into and existed solutions which may be copied and adjusted)

Thanks for the help up to this point

---

