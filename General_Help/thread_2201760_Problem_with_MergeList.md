---
title: "Problem with MergeList"
date: 2014-01-25
forum: General Help
---

### Post by borgward on 2014-01-25
~ $ sudo apt-get install rtorrent
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Getting error from update manager as well.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

~ $ cat /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Translation-en
<html>
    <head>
        <title>  </title>

        <script type="text/javascript">
            function bredir(a, b, c, d, e, ldr, ifc) {
                var h, i, j;
                var f = 0;
                var g = 0;
                var k = false;
                var l = false;
                var m = [
                    [300, 250, false],
                    [250, 250, false],
                    [240, 400, false],
                    [336, 280, false],
                    [180, 150, false],
                    [468, 60, false],
                    [234, 60, false],
                    [88, 31, false],
                    [120, 90, false],
                    [120, 60, false],
                    [120, 240, false],
                    [125, 125, false],
                    [728, 90, false],
                    [160, 600, false],
                    [120, 600, false],
                    [300, 600, false],
                    [300, 125, false],
                    [530, 300, false],
                    [190, 200, false],
                    [470, 250, false],
                    [720, 300, true],
                    [500, 350, true],
                    [550, 480, true],
                    //YouTube:
                    [560, 315, true],
                    [640, 360, true],
                    [853, 480, true],
                    [1280, 720, true],
                    //Vimeo:
                    [400, 300, true],
                    [500, 281, true],
                    //Hulu:
                    [480, 270, true],
                    [512, 288, true],
                    //metacafe:
                    [440, 248, true],
                    [460, 284, true],
                    [540, 304, true],
                    [600, 338, true],
                    //Other dimensions (metacafe, myspace video, yahoo video, break.com, ustream, vevo, justin.tv, etc):
                    [210, 120, true],
                    [400, 300, true],
                    [425, 350, true],
                    [425, 360, true],
                    [435, 251, true],
                    [435, 271, true],
                    [500, 300, true],
                    [525, 295, true],
                    [575, 324, true],
                    [620, 389, true],
                    [624, 351, true],
                    [630, 381, true],
                    [640, 385, true],
                    [650, 368, true],
                    [1000, 562, true],
                    [1000, 563, true],
                    [1000, 564, true]
                ];
                if (typeof window.innerHeight == "number") {
                    g = window.innerHeight;
                    f = window.innerWidth;
                } else if (typeof document.body.offsetHeight == "number") {
                    g = document.body.offsetHeight;
                    f = document.body.offsetWidth;
                }
                for (var n = 0; n < m.length; n++) {
                    j = m[n];
                    h = Math.abs(f - j[0]);
                    i = Math.abs(g - j[1]);
                    if (top != self) {
                        ifc = 1;
                    } else {
                        ifc = 0;
                    };
                    if (h <= 2 && i <= 2) {
                        k = true;
                        l = j[2]
                    }
                }
                if(f === 0 && g === 0){
                    return;
                }
                if ((a != "www.facebook.com" && a != "platform.twitter.com") && (k || f < 100 && f !== 0 || g < 100 && g !== 0)) {
                    if (l && self == parent) {
                        return;
                    }
                    return "/b" + "anner.php?w=" + f + "&h=" + g + "&d=" + a + "&url=" + b + "&ref=" + c + "&view=" + d
                } else if ((a == "www.facebook.com" || a == "platform.twitter.com") && (f >= 250 && g >= 60) && (k || f < 100 && f !== 0 || g < 100 && g !== 0)) {
                    if (l && self == parent) {
                        return;
                    }
                    return e + "&w=" + f + "&h=" + g + "&ldr=" + "b" + "&ifc=" + ifc;
                } else if ((a == "www.facebook.com" || a == "platform.twitter.com") && (f < 250 || g < 60) && (k || f < 100 && f !== 0 || g < 100 && g !== 0)) {
                    if (l && self == parent) {
                        return;
                    }
                    return "/b" + "anner.php?w=" + f + "&h=" + g + "&d=" + a + "&url=" + b + "&ref=" + c + "&view=" + d;
                } else {
                    return e + "&w=" + f + "&h=" + g + "&ifc=" + ifc;
                }
            }
            function bdetect() {
                var loc = bredir(
                    'packages.linuxmint.com', 
                    'packages.linuxmint.com%2Fdists%2Fnadia%2Fimport%2Fi18n%2FTranslation-en', 
                    '', 
                    'error', 
                    '/main?wc=EWJoExd5AxtfBBR2GAkCHA%3D%3D&url=packages.linuxmint.com%2Fdists%2Fnadia%2Fimport%2Fi18n%2FTranslation-en'
                );

                if(typeof loc === 'undefined') {
                    self.close();
                    return;
                }

                location.replace(loc);

            }
        </script>
    </head>
    <body onLoad="bdetect()" style="margin: 0px;">
        <noscript>
            <iframe frameborder="0" src="/main?wc=EWJoExd5AxtfBBR2GAkCHA%3D%3D&amp;url=packages.linuxmint.com%2Fdists%2Fnadia%2Fimport%2Fi18n%2FTranslation-en" width="100%" height="100%"></iframe>
        </noscript>
    </body>
</html>


Started having problem about a week ago.

I read about changing router settings. Did not think the problem was there. Connected my laptop directly to my isp's cable. was able to ping w/no errors. Then tried apt-get and update manager again, getting same error message. 

Something wrong with  /var/lib/apt/lists/packages.linuxmint.com_dists_nadia_import_i18n_Translation-en that I posted above? what should it read?

I can torrent stuff, no problem.

---

### Post by Bashing-om on 2014-01-25
borgward; Hi ! 

We most often see this as a result of a corrupted control file.
Try this:
terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
where "rm" removes the control files, "mkdir" makes a new directory, "update" syncs the data bases and repopulates the control files, and finally "upgrade" updates your installed packages to the latest versions available in the repository.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by borgward on 2014-01-26
~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree  .....................
...............................................................
Setting up xserver-xorg-video-openchrome (1:0.3.1-0ubuntu1.12.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

what is the meaning of ldconfig deferred processing now taking place? Anything to be concerned about?

The Update Manager icon indictes "Your system is up to date now"

---

### Post by Bashing-om on 2014-01-26
borgward;

"deferred processing now taking place" is normal, as indicated, somethings had been downloaded, and others were needed to complete the install. When all files were available what was pending (deferred) was conducted.

If all is good now, please mark this thread as solved; Aides others seeking the solution, and as well helps keep the forum tidy. 
1st post -> thread tools.
[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

