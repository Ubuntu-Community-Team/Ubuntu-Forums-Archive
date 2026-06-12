---
title: "Goolyrics in amaroK not working"
date: 2008-02-04
forum: General Help
---

### Post by money2themax on 2008-02-04
it keeps giving me this error

```

The script 'GoogLyrics' exited with error code: 2

--------------------------

Can't locate WWW/Mechanize.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/money2themax/.kde/share/apps/amarok/scripts/googlyrics/googlyrics line 4.
BEGIN failed--compilation aborted at /home/money2themax/.kde/share/apps/amarok/scripts/googlyrics/googlyrics line 4.

```This is the file in question [or its contents at least]
```

#!/usr/bin/perl
use strict; # Disabled for release version
use warnings;
use WWW::Mechanize;
use IO::File;
use HTML::Entities;
use Text::Iconv;

#Necessary globals
our $mech = WWW::Mechanize->new();
$mech->agent_alias( 'Linux Mozilla' );

#Sites used for URL matching

my %metro = (
    site => "metrolyrics.com",
    name => "Metrolyrics",
    regex => qr/Ringtone \*\*\*<\/a>(.*?)<img/msi,
    disabled => 0,
    plain => 0,
);

my %freel = (
    site => "free-lyrics.net",
    name => "Free-Lyrics",
    regex => qr/<td class="style5" style="font-weight:normal;padding-left:5px;">(.*?)<\/td>/msi,
    disabled => 0,
    plain => 0,
);

my %hotly = (
    site => "hotlyrics.net",
    name => "Hot Lyrics",
    regex => qr/<!-- GOOGLE END \/\/-->(.*?)<script type="text\/javascript">/msi,
    disabled => 0,
    plain => 0,
);
my %leos = (
    site => "leoslyrics.com",
    name => "Leo's Lyrics",
    regex => qr/<font face="Trebuchet MS, Verdana, Arial" size=-1>(.*?)<\/font>/msi,
    disabled => 0,
    plain => 0,
);

my %mma = (
    site => "themadmusicarchive.com",
    name => "The Mad Music Archive",
    regex => qr/<td><span class="Verdana8">(.*?)<\/span>/msi,
    disabled => 0,
    plain => 0,
);

my %lyricspy = (
    site => "lyricspy.com",
    name => "Lyricspy",
    regex => qr/<\/b><br \/>(.*?)<div>/msi,
    disabled => 0,
    plain => 0,
);

my %lyricwiki = (
    site => "lyricwiki.org",
    name => "Lyricwiki",
    regex => qr/<div id="lyric">(.*?)<\/div/msi,
    disabled => 0,
    plain => 0,
);

my %lyriki = (
    site => "lyriki.org",
    name => "Lyriki",
    regex => qr/<\/div>\n<p>(.*?)<\/p>/msi,
    disabled => 0,
    plain => 0,
);

my %lyricsmania = (
    site => "lyricsmania.com",
    name => "Lyricsmania",
    regex => qr/Title: <b>.*?<br><br>(.*?)<script/msi,
    disabled => 0,
    plain => 0,
);

my %letssingit = (
    site => "letssingit.com",
    name => "Let's Sing It",
    regex => qr/<TR class=row2><TD><PRE>(.*)<\/PRE><SPAN class=credits>/msi,
    disabled => 0,
    plain => 1,
);

my %sing365 = (
    site => "sing365.com",
    name => "Sing365",
    regex => qr/Print the Lyrics(.*?)<hr size=1 color=#cccccc>/msi,
    disabled => 0,
    plain => 0,
);

my %azlyrics = (
    site => "azlyrics.com",
    name => "AZLyrics",
    regex => qr/<FONT size=2>.*?<BR>\s*(.*?)\[ <a href="http:\/\/www.azlyrics.com">www.azlyrics.com<\/a> \]<BR><BR>/msi,
    disabled => 0,
    plain => 0,
);

my %l007 = (
    site => "lyrics007.com",
    name => "Lyrics007",
    regex => qr/src=\"http:\/\/pagead2\.googlesyndication\.com\/pagead\/show_ads\.js\">\n<\/script>\n<br><br>(.*?)The hottest songs from/msi,
    disabled => 0,
    plain => 0,
);

my %actionext = (
    site => "actionext.com",
    name => "Actionext",
    regex => qr/<h3>performed by .*?<\/h3>(.*)<div class="foundat">/msi,
    disabled => 0,
    plain => 0,
);

my %songmeanings = (
    site => "songmeanings.net",
    name => "Song Meanings",
    regex => qr/<td width="100%" style="text-align:left;">.*<td width="100%" style="text-align:left;">\s*(.*?)\s*<\/td>/msi,
    disabled => 0,
    plain => 0,
);

my %wearethelyrics = (
    site => "wearethelyrics.com",
    name => "We Are The Lyrics",
    regex => qr/<\/h3>\n<p>\s*(.*?)\s*<\/p>/msi,
    disabled => 0,
    plain => 0,
);

my %mp3bg = (
    site => "mp3-bg.com",
    name => "mp3-bg.com",
    regex => qr/<\/h2><p>(.*?)<ul class="admin">/msi,
    disabled => 0,
    plain => 0,
);

my %mldb = (
    site => "mldb.org",
    name => "MLDb",
    regex => qr/<p class=songtext>(.*?)<\/table>/msi,
    disabled => 0,
    plain => 0,
);

my %justsomelyrics = (
    site => "justsomelyrics.com",
    name => "JUST SOME LYRICS",
    regex => qr/<\/h1>(.*?)<a/msi,
    disabled => 0,
    plain => 0,
);

my %mylyricsbox = (
    site => "mylyricsbox.com",
    name => "MyLyricsBox",
    regex => qr/<div class="songLyrics">(.*?)<\/div>/msi,
    disabled => 0,
    plain => 0,
);

my %megalyrics = (
    site => "megalyrics.ru",
    name => "MegaLyrics",
    regex => qr/<\/script>[[:cntrl:]]*?<br><br>(.*?)<br><a href=\"javascript/msi,
    disabled => 0,
    plain => 0,
);

my %lyricsee = (
    site => "lyrics.ee",
    name => "Lyrics.ee",
    regex => qr|</td></tr> -->*?<br>\n(.*?)<p><br>|msi,
    disabled => 0,
    plain => 0,
);

my %lyricseeprint = (
    site => "lyrics.ee",
    name => "Lyrics.ee (print page)",
    regex => qr|<td height="20"></td>(.*?)</td>|msi,
    disabled => 0,
    plain => 0,
);

my %kovach = (
    site => "kovach.co.yu",
    name => "Kovach",
    regex => qr#>Z</a>.*?<td width="100%" valign="top">(.*?)</td></tr></table>#msi,
    disabled => 0,
    plain => 0,
);

my %local = (
    site => "localhost",
    name => "Local",
    disabled => 0,
    plain => 1,
);

#put references to all the lyrics sites into the hash

my @sites = (\%metro,\%freel,\%hotly,\%leos, \%mma, \%lyricspy, \%lyricwiki, \%lyriki, \%letssingit, \%sing365, \%azlyrics, \%l007, \%actionext, \%songmeanings, \%wearethelyrics, \%mp3bg, \%mldb, \%justsomelyrics, \%mylyricsbox, \%megalyrics, \%lyricsmania, \%lyricsee, \%lyricseeprint, \%kovach);


sub querylyrics {
    my $artist = urldecode(shift);
    my $title = urldecode(shift);

    # This is for local file lyrics
    my $fh = new IO::File;
    my $file = $title . ".txt";
    my $file2 = $artist . " - " . $title . ".txt";
    if ($fh->open("< " . $ENV{"HOME"} . "/lyrics/$file") || $fh->open("< " . $ENV{"HOME"} . "/lyrics/$file2")) {
        my $text = <$fh>;
        $fh->close;
        showlyrics($text, \%local, "http://localhost", $artist, $title);
        return 1;
    }

    $artist =~ s/^The //sgi; #Remove the starting word "The" from artist name, it just causes problems
    $title =~ s/\(.*?\)//sgi;
    $title =~ s/\[.*?\]//sgi;
    if ($artist eq "") {
        $title =~ /(.*) - (.*)/; # try to extract song + artist information.
        if ($1 ne '' && $2 ne '') {
            $artist = $1;
            $title = $2;
        }
    }
    my $attempt = 1;
    while ($attempt != 5) {
    print "\n<br>Attempt #" . $attempt . "\n";
    $mech->get("http://www.google.com/intl/en/");
    if (!$mech->success()) {
        return "connectfail";
    }
    # Try several search queries.
    if ($attempt == 1) {
        $mech->field("q", "lyrics intitle:\"$artist - $title\"", );
    } elsif ($attempt == 2) {
        $mech->field("q", "lyrics \"$artist\" intitle:\"$title\"", );
    } elsif ($attempt == 3) {
        $mech->field("q", "lyrics \"$artist\" \"$title\"", );
    } elsif ($attempt == 4) {
        $mech->field("q", "lyrics $artist $title", );
    }
    $mech->submit();
    foreach ($mech->content() =~ m/<div class=g[\s>].*?<a href=\"(.*?)\"/img) {
        my $url = $_;
        print "\n<br>" . $url . "\n";
        my $o;
        my $ly;
        foreach $ly (@sites) {
            my $urlregex = $ly->{site};
            if ($url =~ m/$urlregex/si) {
                if ($o = scrape($url, $ly, $artist, $title)) {
                    return $o;
                } else {
                    next;
                }
            }
        }
    }
    $attempt = $attempt + 1;
    }
    return "Fail";
}

sub scrape {
    my $loc = shift;
    my $site = shift;
    my $artist = shift;
    my $title = shift;
    if ($site->{disabled}) {
        return 0;
    }
    $mech->get($loc);
    if (!$mech->success()) {
        return 0; #Assume the user _does_ have an internet connection since a previous test has happened on google, let's just say the lyrics site is down.
    }
    my @cont_type = $mech->response()->content_type;
    $cont_type[1]=~ s/charset=(.*)/$1/ig; # Get the charset of the response
    my $char_converter = Text::Iconv->new($cont_type[1], "UTF-8"); # Convert the response to UTF-8
    my $current = $mech->content();
    my $regex = $site->{regex};
    if ($current =~ $regex) {
        print "\n<br>Regex success for " . $site->{name} . "\n";
        showlyrics($char_converter->convert($1), $site, $loc, $artist, $title);
        return 1;
    } else {
        print "\n<br>Regex failed for " . $site->{name} . "\n";
        return 0;
    }
}

while (1) {
    my $message = <STDIN>;
    chomp($message);
    if ($message =~ /^configure/) {
        system("dcop", "amarok", "playlist", "popupMessage", "This script does not require any configuration.");
    } elsif ($message =~ /^fetchLyrics/) {
        my @tofetch = split(/ /, $message);
        my $artist = urldecode($tofetch[1]);
        my $title = urldecode($tofetch[2]);
        my $out = querylyrics($artist, $title);
        if ($out eq "Fail") {
            system("dcop", "amarok", "contextbrowser", "showLyrics", "<?xml version=\"1.0\" encoding=\"UTF-8\" ?> <suggestions page_url=\"http://www.google.org\">Failed to find any lyrics. Press refresh to try again.</suggestions>");
        } elsif ($out eq "connectfail") {
            system("dcop", "amarok", "contextbrowser", "showLyrics", ""); #communications errror, "send an empty string"
        }
    }
}

sub showlyrics {
    my $out = shift;
    my $site = shift;
    my $loc = shift;
    my $artist = shift;
    my $title = shift;
    if ($site->{plain}) {
        $out = striphtml($out);
    } else {
        $out = striphtml(htmllinebreak($out));
    }
    $out =~ s/^\s+|\s+$//g; #Kills leading and trailing whitespace.
    $out =~ s/\[.*? lyrics on http:\/\/www\.metrolyrics\.com\]\n//g; #metrolyrics: we're sick of your ********.
    print $out . "\n";
    my $doc = "<?xml version=\"1.0\" encoding=\"UTF-8\" ?> <lyrics site=\"" . encode_entities($site->{name}) ."\" site_url=\"" . encode_entities($site->{site}) . "\" page_url=\"" . encode_entities($loc) . "\" artist=\"" . filter($artist) . "\" title=\"" . filter($title) . "\">" . filter($out) . "</lyrics>";
    system("dcop", "amarok", "contextbrowser", "showLyrics", $doc);
}
sub htmllinebreak {
    my $out = shift;
    $out =~ s/\n//sgi; #Kill normal linebreaks, we're going HTML :)
    $out =~ s/<br>/\n/sgi;
    $out =~ s/<br *\/?>/\n/sgi;
    return $out;
}

sub filter {
    my $text = shift;
    $text =~ s/&/&amp;/go;
    $text =~ s/</&lt;/go;
    $text =~ s/>/&gt;/go;
    $text =~ s/'/&apos;/go;
    $text =~ s/`/&apos;/go;
    $text =~ s/&#8217;/&apos;/go;
    $text =~ s/"/&quot;/go;
    return $text;
}

sub urldecode {
  my $str = shift;
  $str =~ s/%([A-Fa-f0-9]{2})/pack('C', hex($1))/seg;
  return $str;
}

sub striphtml {
    my $str = shift;
    $str =~ s/\<[^\<]+\>//g;
    return $str;
}


```this might help too
```

Sick and tired of traditional, crappy lyrics search tools? Sick of having to go to google yourself to hunt down lyrics? GoogLyrics is for you! I've been annoyed by the low yield on 
some of my more obscure music with many of the Amarok lyric search scripts available. A long time ago, I'd seen a rather impressive windows program called EvilLyrics, they had 
an interesting idea, search for the lyrics then rip them off known websites, using this it managed to have a very high success rate at lyric extraction. I decided to implement this 
myself in an amarok script. After a quick day of scripting, here's the result: a true lyrics metasearch script. Now a month later, this script is constantly getting more advanced. It 
now supports many different popular lyrics sites and has an extremely high success rate on even my more obscure music. If you're using Ubuntu or debian, this is as simple as 
download+install the package below. For any other distro, read on. This script requires the WWW::Mechanize perl module to run, to install it on any distro: # cpan cpan> install 
WWW::Mechanize Done. Text::Iconv is also required for this, however, this is already included in most perl packages. if not, follow the cpan instructions replacing 
WWW::Mechanize with Text::Iconv
()

```

---

### Post by money2themax on 2008-02-04
Bump!

---

### Post by money2themax on 2008-02-05
bump please help me with this i don't know much about perl

---

### Post by kuja on 2008-02-05
Well, I'd do what the thing in your second quoteblock says and try to install the perl modules needed: (Note: they may take a really long time to complete, with no indication of progress)

```
sudo -s
cpan cpan> install WWW::Mechanize Done
cpan cpan> install Text::Iconv Done
exit
```

If that fails to work, I'd suggest giving **wiki-lyrics** a try.

---

### Post by money2themax on 2008-02-05
thx i tried it and this happened

```

money2themax@MX-Ubuntu-000:~$ sudo -s
root@MX-Ubuntu-000:~# cpan cpan> install WWW::Mechanize Done
# Testing WWW::Mechanize 1.34, with LWP 5.805, Perl 5.008008, /usr/bin/perl
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
Parsing of undecoded UTF-8 will give garbage when decoding entities at /usr/lib/perl5/HTML/PullParser.pm line 83.
# Started http://localhost:50434/
# Started http://localhost:59483/
# Started http://localhost:41387/
# Started http://localhost:34941/
# Started http://localhost:45151/
# Started http://localhost:42178/
# Started http://localhost:58887/
# Started http://localhost:55886/
# Started http://localhost:42727/
# Started http://localhost:53904/

```
EDIT: it seems to be working fine

---

### Post by kuja on 2008-02-05
I presume this means its still not working? I really don't know what the problem could be .... though at least it's forward progress seeing as you're now getting a differerent error eh? 

I'd go on kde-apps.org and ask the scripts developer directly .... I've no idea how to fix the problem.

On the other hand, I still say using something the wiki-lyrics script instead  (which sounds very similar) at least in the meantime whle you try to figure out whats up with the other one would probably be a functional idea.

---

### Post by money2themax on 2008-02-05
> **kuja said:**
> I presume this means its still not working? I really don't know what the problem could be .... though at least it's forward progress seeing as you're now getting a differerent error eh? 

I'd go on kde-apps.org and ask the scripts developer directly .... I've no idea how to fix the problem.

On the other hand, I still say using something the wiki-lyrics script instead  (which sounds very similar) at least in the meantime whle you try to figure out whats up with the other one would probably be a functional idea.
it's working yes but i can't use wiki-lyrics it just won't contact the server but now that i installed that perl thing goolyrics seems to be working perfectally

---

### Post by metalcoat on 2008-02-15
To help people who stumble by this thread a simple 
```
sudo apt-get install libtest-www-mechanize-perl 
```
will work too.

---

### Post by Vajk on 2008-02-22
> **metalcoat said:**
> To help people who stumble by this thread a simple 
```
sudo apt-get install libtest-www-mechanize-perl 
```
will work too.

thanks, it worked for me too

---

### Post by Auslegung on 2008-03-26
> **metalcoat said:**
> To help people who stumble by this thread a simple 
```
sudo apt-get install libtest-www-mechanize-perl 
```
will work too.


Works great, thanks man.  It was kinda funny, I was listening to a slightly obscure song and  as soon as I stopped my old lyrics script and started Googlyrics, the correct lyrics popped up.

---

### Post by Mithrilhall on 2008-03-26
> 
sudo apt-get install libtest-www-mechanize-perl


Thanks...worked perfectly.

---

### Post by samgod2001 on 2008-04-07
> **metalcoat said:**
> To help people who stumble by this thread a simple 
```
sudo apt-get install libtest-www-mechanize-perl 
```
will work too.

also worked perfectly for me too!

---

### Post by Insperatus on 2008-05-12
> **metalcoat said:**
> To help people who stumble by this thread a simple 
```
sudo apt-get install libtest-www-mechanize-perl 
```
will work too.

Running Amarok 1.4.9.1 under Gnome 2.22.1 all with Ubuntu 8.04

This easy solution for GoogLyrics worked great thanks! :guitar:

---

