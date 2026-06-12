---
title: "Scripting error when extracting data from multiple files using kappa (Starlink)"
date: 2013-11-08
forum: General Help
---

### Post by k.a.tree on 2013-11-08
Hello,

I am a relative newbie to Ubuntu so please excuse my question if it seems too simple or if it is posted in the wrong section!

I am using the analysis package 'Starlink' to analyse a large amount of image files. The code that I have scripted is:

#!/bin/csh -f


[COLOR=#ff0000]source $STARLINK_DIR/etc/cshrc[/COLOR]
[COLOR=#ff0000]source $STARLINK_DIR/etc/login[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]alias echo "echo > /dev/null"[/COLOR]
[COLOR=#ff0000]kappa[/COLOR]
[COLOR=#ff0000]unalias echo[/COLOR]


alias sex $EXTRACTOR_DIR/sex

cd /home/astro/Documents/dSct-20Jun2013-1
cp /home/astro/Documents/dSct-20Jun2013-1/default.param .
cp /star/star-hikianalia/bin/extractor/config/default.conv .
cp /home/astro/Documents/dSct-20Jun2013-1/default.sex .


foreach img (`ls dSct*.fits`)    #dSct-20Jun2013-V-099.fits
    set rootname = `echo $img | sed s/.fits//`
    set time = `fitsval $img JD`
    echo "date is $time"
    set outfile = $rootname".csv"
    echo $rootname $outfile
    sex $img -CATALOG_NAME $outfile -DETECT_THRESH 10
end


When I run this script in terminal, the following lines are returned:

cp: `/home/astro/Documents/dSct-20Jun2013-1/default.param' and `./default.param' are the same file
cp: `/home/astro/Documents/dSct-20Jun2013-1/default.sex' and `./default.sex' are the same file

If I run the script without the lines coloured [COLOR=#ff0000]red, [/COLOR]the script runs without a hitch and the required .csv files are produced. The problem lies with the [COLOR=#ff0000]red[/COLOR] lines of code.

Any suggestions please?

---

