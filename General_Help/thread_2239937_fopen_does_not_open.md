---
title: "fopen does not open"
date: 2014-08-16
forum: General Help
---

### Post by chris137 on 2014-08-16
Hi,
so I got this php-code which is supposed to open a certain URL if the link is clicked.
Before I did not have $open at all but the link directly at fopen(xxx).
Since this did not work I tried to outsource it which does not work either.
For testing purposes the Link now acutally leads to the destination.
Removing  $open from the href or replacing it with e.g. # does not work.
```
foreach($fritz as $fcurrent) {
     $ain = $fcurrent[0];
     $name = $fcurrent[1];
    
     $fstate = file_get_contents("http://fritz.box//webservices/homeautoswitch.lua?ain=$ain&switchcmd=getswitchstate");
     if ($fstate == 0) {
             $statef = "on";
     }
     else {
             $statef = "off";
     }
     $open = "http://fritz.box//webservices/homeautoswitch.lua?ain=$ain&switchcmd=setswitch$statef";
     echo '<script type="text/javascript">
     function doSomething() {
          var handle = fopen($open);
             fclose(handle);
         return false;
     }
     </script>';
     echo '<a href="'. $open .'" onclick="doSomething()">';
     echo "<div class=\"entry state" . $fstate . "\">";
     echo "<div class=switch></div>";^M
     echo "<span class=info>Fritz!DECT - $name</span>";^M
     echo "<span class=channel></span>";^M
     echo "</div>\n";^M
     echo "</a>\n";
    
     $findex++;
     }
```

I am pretty sure the issue is produced by the wrong usage of qoutes but I just can'get behind it.

Any ideas on that?

Edit:
Too it out of javascript and use it directly in php-code.
Works now.
Looks like this does not work at all in javascript.

---

