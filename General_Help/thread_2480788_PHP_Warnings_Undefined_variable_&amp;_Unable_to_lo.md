---
title: "PHP Warnings: Undefined variable &amp; Unable to load dynamic library"
date: 2022-11-10
forum: General Help
---

### Post by nickdc on 2022-11-10
Attempting to update my partner's website, untouched since 2018 due to a stroke. First objective: a functioning local test site. I'm moderately tech confident but can't read code.

I've fresh installed Ubuntu 22.04.1 as a guest on VirtualBox running on my Manjaro Gnome host machine and installed the LAMP stack, with MariaDB rather than MSQL and PHP 8.1. Didn't install MyPHPadmin. Verified setup working, then downloaded all the files from the live site with Filezilla and put them in /var/www/html. Everything works except for the display of images of artwork when called for from any of the relevant links. Since it all works fine on the live site (diclay.co.uk) I'm assuming the problem is not with the code on any of the pages but with the configuration of either apache2 or PHP. And that's where I quickly get out of my depth.

I suspect the much repeated lines in the Apache2 error log ```
[Thu Nov 10 11:35:21.982557 2022] [php:warn] [pid 3995] [client 127.0.0.1:56034] PHP Warning:  Undefined variable $selected in /var/www/html/php/includes/main.php on line 33, referer: http://localhost/
``` is referring to the issue and crops up every time I click on an artwork link. The relevant section of main.php, containing line 33, is this:

[PHP]
// Used for testing purposes. e.g. if on local server put /diclay/ for address http://localhost/diclay/. If not in sub folder put /
$home = "/"; //   /diclay/

foreach($menuArray as $menuItemKey => $menuItem) {
    if( $menuItemKey == $IncludeVar1 ) {
        $selected = "id='selected'";
    } elseif( (true == $IncludeVar2) && ($menuItemKey == "since2000") ) {
        $selected = "id='selected'";
    }
    echo "<li><a href='$home$menuItemKey.php' $selected>$menuItem</a></li>\n";
    $selected = NULL;
}

// <li><a href="" id="selected">Links</a></li>
?>

        </ul><br />
    </div>
<?php if($IncludeVar2 == True) { ?>    
    <div id="navWrap2">
        <ul id="navigation2">[/PHP]

Line 33 is the <echo> line.

The PHP error log also has a much repeated line: ```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/local/lib/php/extensions/no-debug-non-zts-20060613/suhosin.so' - /usr/local/lib/php/extensions/no-debug-non-zts-20060613/suhosin.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

I strongly suspect the two errors have a common source and it would be a simple matter to clear up for anyone with an understanding of the relevant code. I'm hoping some kind soul with such an understanding might come to my rescue.

---

### Post by Holger_Gehrke on 2022-11-10
suhosin was a module for PHP 5 that is meant to harden a PHP installation against the exploitation of most know and some potential weaknesses. The original suhosin.so doesn't work on newer version of PHP. There's a successor to suhosin called suhosin NG but AFAIK there's no easy way to install that, you'd have to compile it yourself. If you just want to get rid of the error message, you can disable the loading of the extension in the php.ini.

The other error is down to a change in how PHP handles undefined variables. In old versions variables were defined and initialized when first used, so "$selected" in line 33 would output an empty string if neither of the conditions in the "if" and "elseif" stanzas were true. This led to interesting and hard to find errors if you had a typo in a variable name. So in newer versions you have to define a variable before using it. Move the line '$selected=NULL' up between the 'foreach ...' and 'if ...' lines. That way '$selected' is defined and the error should go away.

Holger

---

### Post by nickdc on 2022-11-10
Thanks very much for your help. 

I'm not too bothered about the suhosin issue if it's not critical to operation. 

I've edited the main.php file as you suggested and indeed the error messages in the log have stopped ... but the pages still don't load! Grr! I thought the "undefined variable" was the problem, but obviously not. Now I'm clueless as to how to troubleshoot further. I'm sure it's a simple configuration issue somewhere on the server stack as everything loads fine except all those links to the artwork pages. They all bring up the Apache "404 Not Found" page.

---

### Post by norobro on 2022-11-11
> **nickdc said:**
>  Everything works except for the display of images of artwork when called for from any of the relevant links. Since it all works fine on the live site (diclay.co.uk) It looks like something is wrong with your local site directory structure. Your error log should tell you where the server is looking for those artwork files. 

Alternatively, look at the console tab under "developer tools" in your browser.

---

### Post by nickdc on 2022-11-12
> **norobro said:**
> It looks like something is wrong with your local site directory structure. Your error log should tell you where the server is looking for those artwork files. 

Alternatively, look at the console tab under "developer tools" in your browser.

Thanks for this. The only error log I can find is in /var/log/apache2 and that doesn't show anything problematic. Nor does the console tab in DT. However, your comment on the directory structure had me look again at one of the key folders and that has led to some progress, along with further confusion:

Looking in the browser (Firefox) at the source for the Artwork Gallery page ```
http://localhost/artworkGallery.php
``` it looks as though all the links to bring up the individual artwork pages are listed at the bottom of the page: 
[PHP] <h2>Artwork Gallery</h2>
    
    <ul class="fullGallery">
        <li ><a id='ALrose' href='artwork/rose'><span>Rose</span></a></li>
    <li ><a id='ALallTheWoolMyMotherNeverKnittedMakingTime' href='artwork/allTheWoolMyMotherNeverKnittedMakingTime'><span>All the wool my mother never knitted - Making Time</span></a></li>
    <li ><a id='ALdeparture' href='artwork/departure'><span>Departure</span></a></li>
    <li ><a id='ALtheLongThread' href='artwork/theLongThread'><span>The Long Thread</span></a></li>
    <li ><a id='ALresponse' href='artwork/response'><span>Response</span></a></li>
    <li ><a id='ALallTheWoolMyMotherNeverKnittedSedition' href='artwork/allTheWoolMyMotherNeverKnittedSedition'><span>All the wool my mother never knitted - Sedition</span></a></li>
    <li ><a id='ALallTheWoolMyMotherNeverKnitted' href='artwork/allTheWoolMyMotherNeverKnitted'><span>All the wool my mother never knitted</span></a></li>
    <li ><a id='ALyouLookingAtMe' href='artwork/youLookingAtMe'><span>You Looking At Me</span></a></li>
    <li ><a id='ALpolepole' href='artwork/polepole'><span>Polepole</span></a></li>
    <li ><a id='ALreturnJourney' href='artwork/returnJourney'><span>Return Journey</span></a></li>
    <li ><a id='ALonYourMindCarlisle' href='artwork/onYourMindCarlisle'><span>On your mind - Carlisle</span></a></li>
    <li ><a id='ALonYourMindDubrovnik' href='artwork/onYourMindDubrovnik'><span>On your mind - Dubrovnik</span></a></li>
    <li ><a id='ALladder' href='artwork/ladder'><span>Ladder</span></a></li>
    <li ><a id='ALsingingMountAbora' href='artwork/singingMountAbora'><span>Singing of Mount Abora</span></a></li>
    <li ><a id='ALsoundingsJerusalem' href='artwork/soundingsJerusalem'><span>Soundings Jerusalem</span></a></li>
    <li ><a id='ALunderHisHat' href='artwork/underHisHat'><span>Under his hat</span></a></li>
    <li ><a id='ALsoundings' href='artwork/soundings'><span>Soundings</span></a></li>
    <li ><a id='ALsuffolkTerritory' href='artwork/suffolkTerritory'><span>Suffolk Territory</span></a></li>
    <li ><a id='ALwheelchairJourneys' href='artwork/wheelchairJourneys'><span>Wheelchair journeys</span></a></li>
    <li ><a id='ALonYourMindIpswich' href='artwork/onYourMindIpswich'><span>On your mind - Ipswich</span></a></li>
    <li ><a id='ALeggOnMyFace' href='artwork/eggOnMyFace'><span>Egg on my face</span></a></li>
    <li ><a id='ALonYourMindTelAviv' href='artwork/onYourMindTelAviv'><span>On your mind - Tel Aviv</span></a></li>
    <li ><a id='ALconflict' href='artwork/conflict'><span>Conflict</span></a></li>
    <li ><a id='ALpondSketch' href='artwork/pondSketch'><span>Pond Sketch</span></a></li>
    <li ><a id='ALwater' href='artwork/water'><span>Water</span></a></li>
    <li ><a id='ALsoundingsKrakow' href='artwork/soundingsKrakow'><span>Soundings Krakow</span></a></li>
    <li ><a id='ALsoundingsWALL' href='artwork/soundingsWALL'><span>Soundings - WALL</span></a></li>
    <li ><a id='ALtower' href='artwork/tower'><span>Tower</span></a></li>
    <li ><a id='ALsurvival' href='artwork/survival'><span>Survival</span></a></li>
    <li ><a id='ALsoundingsWALLCarlisle' href='artwork/soundingsWALLCarlisle'><span>Soundings - WALL (Carlisle)</span></a></li>
    <li ><a id='ALjoining' href='artwork/joining'><span>Joining</span></a></li>
    <li ><a id='ALlondonTerritory' href='artwork/londonTerritory'><span>London territory</span></a></li>
    <li ><a id='ALbasement' href='artwork/basement'><span>Basement</span></a></li>
    <li ><a id='ALsoundingsCarlisle' href='artwork/soundingsCarlisle'><span>Soundings Carlisle</span></a></li>
    <li ><a id='ALtouchExperiment' href='artwork/touchExperiment'><span>Touch Experiment</span></a></li>
    <li ><a id='ALterritories' href='artwork/territories'><span>Territories map 1</span></a></li>
    <li ><a id='ALsoundingsLanternHouse' href='artwork/soundingsLanternHouse'><span>SOUNDINGS</span></a></li>
    <li ><a id='ALflyOnTheWall' href='artwork/flyOnTheWall'><span>Fly On The Wall</span></a></li>
    <li ><a id='ALafricanTakeAway' href='artwork/africanTakeAway'><span>African Take Away</span></a></li>
    <li ><a id='ALuntitledPerformance' href='artwork/untitledPerformance'><span>Untitled performance</span></a></li>
    <li ><a id='ALlondonTouchExperiment' href='artwork/londonTouchExperiment'><span>London Touch Experiment</span></a></li>
    <li ><a id='ALsilverCar' href='artwork/silverCar'><span>Silver Car</span></a></li>
    </ul>

</div>

</div>
[/PHP]
 
And each of those links, eg  <href='artwork/silverCar'> suggests a two tier structure. In the artwork folder however (/var/www/html/artwork) the folders containing the images and notes for each artwork page were inside a folder called "images". So I tried copying those folders directly into the "artwork" folder, which proved successful: instead of a 404 page those links (eg [http://localhost/artwork/silverCar/](http://localhost/artwork/silverCar/)) now return what I'd call a "skeleton page", like this:

```
**Index of /artwork/silverCar**

   [TABLE]
[TR]
[TH][IMG]http://localhost/icons/blank.gif[/IMG][/TH]
[TH][Name]("http://localhost/artwork/silverCar/?C=N;O=D")[/TH]
[TH][Last modified]("http://localhost/artwork/silverCar/?C=M;O=A")[/TH]
[TH][Size]("http://localhost/artwork/silverCar/?C=S;O=A")[/TH]
[TH][Description]("http://localhost/artwork/silverCar/?C=D;O=A")[/TH]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[TR]
[TD][IMG]http://localhost/icons/back.gif[/IMG][/TD]
[TD][Parent Directory]("http://localhost/artwork/")[/TD]
[TD][/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://localhost/icons/unknown.gif[/IMG][/TD]
[TD][Thumbs.db]("http://localhost/artwork/silverCar/Thumbs.db")[/TD]
[TD="align: right"]2022-11-09 16:34[/TD]
[TD="align: right"]8.0K[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://localhost/icons/image2.gif[/IMG][/TD]
[TD][dni_silverCar_tn.jpg]("http://localhost/artwork/silverCar/dni_silverCar_tn.jpg")[/TD]
[TD="align: right"]2022-11-09 16:34[/TD]
[TD="align: right"] 12K[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][IMG]http://localhost/icons/image2.gif[/IMG][/TD]
[TD][silverCar.jpg]("http://localhost/artwork/silverCar/silverCar.jpg")[/TD]
[TD="align: right"]2022-11-09 16:34[/TD]
[TD="align: right"] 21K[/TD]
[TD][/TD]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]
 Apache/2.4.52 (Ubuntu) Server at localhost Port 80

```

That page displays properly on the live site: [http://diclay.co.uk/artwork/silverCar](http://diclay.co.uk/artwork/silverCar)

But that leaves me still with two unresolved issues: First, the live site has the   artwork/images/folder-for-each-artwork   structure and apache has no problem finding its way through the redundant "images" folder. Secondly, having removed that layer on the test site, why is apache not now rendering the pages fully?

Another bit of progress is that I've checked with the hosting company and they  helpfully switched to PHP 8.1 on the live site (it was on 5.6!), after  which I expected the same pages to fail, but actually it all worked fine, so that rules out PHP version differences causing the problem.

---

### Post by nickdc on 2022-11-13
Digging back into early correspondence with the guy who created the website, I'm reminded that there was a similar problem when PHP evolved between versions and register_globals was defaulted from "on" to "off". Switching it back on got the site fully functioning again. But register_globals has long since disappeared, so how should PHP be configured to enable pages that depended on register_globals being on to function? I've tried googling this but quickly get out of my depth.

---

### Post by nickdc on 2022-11-14
Finally got there! I always suspected it was a simple configuration issue. Editing the apache2.conf file and changing all instances of "Override None" to "Override All" got everything working again as it should.

---

