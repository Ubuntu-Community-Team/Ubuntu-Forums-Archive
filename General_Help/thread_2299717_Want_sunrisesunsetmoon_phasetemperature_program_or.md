---
title: "Want sunrise/sunset/moon phase/temperature program or desktop widget"
date: 2015-10-20
forum: General Help
---

### Post by michael-piziak on 2015-10-20
I want sunrise/sunset/moon phase/temperature program or desktop widget.

If it's an app or program, I can put it in startup upon boot up.

12.04 lts

---

### Post by michael-piziak on 2015-10-20
Perhaps something on this page?
I'd like to have one of them that does everything I mentioned.
Please suggest.

link:
[http://askubuntu.com/questions/149707/is-there-a-desktop-weather-app](http://askubuntu.com/questions/149707/is-there-a-desktop-weather-app)

p.s. I see at least one uses Gnome, will that work under Ubuntu Unity > ?

---

### Post by Lars Noodén on 2015-10-20
Are you using conky?  

I used a variant of this moonphase script in the past.  It needs the addition of Astro/MoonPhase from CPAN.  

```

#!/usr/bin/perl -w

use strict;
use integer;

use Astro::MoonPhase;

foreach my $t ( -28..128 ) {

    my $d = 86400 * $t;

my ( $MoonPhase,
     $MoonIllum,
     $MoonAge,
     $MoonDist,
     $MoonAng,
     $SunDist,
     $SunAng ) = phase(time()+$d);

    print scalar localtime( time()+$d ),"\n";
    print  "MoonPhase\t $MoonPhase\n";
    print  "MoonIllum\t $MoonIllum\n";
    print  "MoonAge  \t $MoonAge\n";
    print  "MoonDist \t $MoonDist\n";
    print  "MoonAng \t $MoonAng\n";
    print  "SunDist \t $SunDist\n";
    print  "SunAng  \t $SunAng\n";
    print qq(\n);
    
    if  (1 ) {
        my @phases = phasehunt();
        print "New Moon      = ", scalar(localtime($phases[0])), "\n";
        print "First quarter = ", scalar(localtime($phases[1])), "\n";
        print "Full moon     = ", scalar(localtime($phases[2])), "\n";
        print "Last quarter  = ", scalar(localtime($phases[3])), "\n";
        print "New Moon      = ", scalar(localtime($phases[4])), "\n";
    }

print qq(\n);
print qq(\n);
}


```

You can modify it as you see fit, I wrote it about 10 years ago.

---

### Post by michael-piziak on 2015-10-20
> **Lars Noodén said:**
> Are you using conky?  

I used a variant of this moonphase script in the past.  It needs the addition of Astro/MoonPhase from CPAN.  

```

#!/usr/bin/perl -w

use strict;
use integer;

use Astro::MoonPhase;

foreach my $t ( -28..128 ) {

    my $d = 86400 * $t;

my ( $MoonPhase,
     $MoonIllum,
     $MoonAge,
     $MoonDist,
     $MoonAng,
     $SunDist,
     $SunAng ) = phase(time()+$d);

    print scalar localtime( time()+$d ),"\n";
    print  "MoonPhase\t $MoonPhase\n";
    print  "MoonIllum\t $MoonIllum\n";
    print  "MoonAge  \t $MoonAge\n";
    print  "MoonDist \t $MoonDist\n";
    print  "MoonAng \t $MoonAng\n";
    print  "SunDist \t $SunDist\n";
    print  "SunAng  \t $SunAng\n";
    print qq(\n);
    
    if  (1 ) {
        my @phases = phasehunt();
        print "New Moon      = ", scalar(localtime($phases[0])), "\n";
        print "First quarter = ", scalar(localtime($phases[1])), "\n";
        print "Full moon     = ", scalar(localtime($phases[2])), "\n";
        print "Last quarter  = ", scalar(localtime($phases[3])), "\n";
        print "New Moon      = ", scalar(localtime($phases[4])), "\n";
    }

print qq(\n);
print qq(\n);
}


```

You can modify it as you see fit, I wrote it about 10 years ago.

I have seen Conky in the Ubuntu magazine (Full Circle magazine); however, I don't have a clue how to get this Conky on my system.
Also, I would like to have the moon phases and sun set and rise in the Conky too.

If you or someone can help me pull this Conky off with the features I want, i would much appreciate it!

---

### Post by Lars Noodén on 2015-10-20
There's a whole thread about conky screen shots with matching .conkyrc files.  That's the best place probably.  My conkyrc is rather primitive and probably wrongish.

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

