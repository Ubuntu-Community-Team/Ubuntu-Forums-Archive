---
title: "Problem With A Perl Script"
date: 2013-11-28
forum: General Help
---

### Post by turkel.christopher on 2013-11-28
I found this script to download and display weather from weather.com:

```
#!/usr/bin/perl
use strict;
use LWP::Simple;
my $content = get("http://www.weather.com/weather/print/01225");
$content =~ s/.*<!-- begin loop -->(.*)<!-- end loop -->.*/$1/s;
my @day = split /<TR>/, $content;
shift @day;
my ($day, $date, $img, $temp, $precip);
my $tomorrow;
foreach $_ (@day) {
    ($day) = /(\w+)<\/A>/s;
    ($date) = /<BR> (.+?)</s;
    ($img) = /(\d+)\.gif/s;
    $img = $ARGV[0] . $img . '.png';
    ($temp) = /<B>(.*?)<\/B>/s;
    $temp =~ s/&deg;/chr(186)/eg;
    $temp =~ s|(\d+)|sprintf "%d", ($1 - 32) * 5 / 9|eg;
    ($precip) = /(\d+ %)/;
    print $img . "\n" . $temp . "C\n" . $precip . "\n";
}

```

It displays temps in Celsius but since I am American I need it in Fahrenheit. Any help? I am a perl noob.

---

### Post by SantaFe on 2013-11-28
I don't know perl either, but it looks like it's pulling the Degrees in Fahrenheit & converting it TO Celsius.  The conversion rule is C= (F-32)x5/9.  And if you look at this line, you can see it's using that to get the final Degree output.

$temp =~ s|(\d+)|sprintf "%d", **($1 - 32) * 5 / 9**|eg;

Maybe someone out there can show how to change it to remove the conversion formula?    

But that's just a wild guess, hopefully someone who knows Perl will step up and Knit you a solution. ;)

---

### Post by efflandt on 2013-11-29
SantaFe gave you a clue. Just comment out or remove the line that converts degrees F to C. I also commented out the last existing line of the loop to show you that I changed the C to F in a replicated line. When you modify code like that and it works, the commented lines can be deleted:```
#!/usr/bin/perl
use strict;
use LWP::Simple;
my $content = get("http://www.weather.com/weather/print/01225");
$content =~ s/.*<!-- begin loop -->(.*)<!-- end loop -->.*/$1/s;
my @day = split /<TR>/, $content;
shift @day;
my ($day, $date, $img, $temp, $precip);
my $tomorrow;
foreach $_ (@day) {
    ($day) = /(\w+)<\/A>/s;
    ($date) = /<BR> (.+?)</s;
    ($img) = /(\d+)\.gif/s;
    $img = $ARGV[0] . $img . '.png';
    ($temp) = /<B>(.*?)<\/B>/s;
    $temp =~ s/&deg;/chr(186)/eg;
#    $temp =~ s|(\d+)|sprintf "%d", ($1 - 32) * 5 / 9|eg;
    ($precip) = /(\d+ %)/;
#    print $img . "\n" . $temp . "C\n" . $precip . "\n";
    print $img . "\n" . $temp . "F\n" . $precip . "\n";
}
```

---

### Post by turkel.christopher on 2013-11-29
Thank you!

---

