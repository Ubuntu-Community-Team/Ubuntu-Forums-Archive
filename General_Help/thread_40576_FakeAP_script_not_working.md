---
title: "FakeAP script not working"
date: 2005-06-09
forum: General Help
---

### Post by sjlsam on 2005-06-09
i downloaded this script (along with the hostap drivers required), but i cannot even get the script to define it's variables right

terminal keeps returning:
```
root@linuxlap:/home/sam/Desktop/fakeap # /home/sam/Desktop/fakeap/fakeap.pl
/home/sam/Desktop/fakeap/fakeap.pl: line 16: use: command not found
/home/sam/Desktop/fakeap/fakeap.pl: line 17: use: command not found
/home/sam/Desktop/fakeap/fakeap.pl: line 18: use: command not found
/home/sam/Desktop/fakeap/fakeap.pl: line 19: use: command not found
/home/sam/Desktop/fakeap/fakeap.pl: line 21: use: command not found
/home/sam/Desktop/fakeap/fakeap.pl: line 22: syntax error near unexpected token `$sleep_opt'
/home/sam/Desktop/fakeap/fakeap.pl: line 22: `  qw( $sleep_opt $channel_opt $mac_opt $essid_opt $words_opt $interface_opt $vendors_opt $wep_opt $key_opt $power_opt );'
```

why cant the USE command work.. was it removed in the most recent version of perl?

```
#
# fakeap - Create fake 802.11b Access Points 
# Stuart Stock and Ken Beames, Black Alchemy Weapons Lab
# $Id: fakeap.pl,v 1.3 2002/08/31 20:56:42 shstock Exp $
#
# Copyright (c) 2002 Black Alchemy Enterprises.  All rights reserved.
# This code is released under the GNU Public License.
# --------------------------------------------------------------------
# Notes:
#
# Requires the CVS version (as of 7/31/2002) of the Prism2/2.5/3 Host AP
# driver to switch BSSID (MAC address).  If you use an older version,
# the MAC address change will appear to work, but the beacons will retain
# the original address.

use strict;
use warnings;
use Getopt::Long;
use Time::HiRes;

use vars
  qw( $sleep_opt $channel_opt $mac_opt $essid_opt $words_opt $interface_opt $vendors_opt $wep_opt $key_opt $power_opt );

my $MAX_CHANNEL = 11;                 # Noth America.  Change for other regions.
my $IWCONFIG    = "/sbin/iwconfig";                      # Change as needed
my $IFCONFIG    = "/sbin/ifconfig";                      # Change as needed
my $CRYPTCONF   = "/usr/local/bin/hostap_crypt_conf";    # Change as needed

my @words = ( "Access Point", "tsunami", "host", "airport", "linksys" );
my @vendors = ( "00:00:0C:", "00:00:CE:", "00:00:EF:" );

# catch ctrl-c
#
$SIG{INT} = \&int_catcher;

# int_catcher
#
# args: none
# rets: none
#
# Signal catcher.  Prints message and exits.

sub int_catcher {
    print "\n";
    print "-------------------------------------------------------------------------\n";
    print "Run complete\n\n";

    exit;

}

# usage
# 
# args: none
# rets: none
#
# Prints arguments and exits

sub usage {
    print "Usage: fakeap.pl --interface wlanX [--channel X] [--mac XX:XX...]\n";
    print "     [--essid NAME] [--words FILENAME] [--sleep N] [--vendors FILENAME]\n";
    print "     [--wep N] [--key KEY] [--power N]\n\n";

    print "     --channel X     Use static channel X\n";
    print "     --essid NAME    Use static ESSID NAME\n";
    print "     --mac XX:XX...  Use static MAC address XX:...\n";
    print "     --words FILE    Use FILE to create ESSIDs \n";
    print "     --sleep N       Sleep N Ssec between changes, default 0.25\n";
    print "     --vendor FILE   Use FILE to define vendor MAC prefixes \n";
    print "     --wep N         Use WEP with probability N where 0 < N <= 1\n";
    print "     --key KEY       Use KEY as the WEP key.  Passed raw to iwconfig\n";
    print "     --power N       Vary Tx power between 1 and N.  In milliwatts\n";
    print "\n";
}

# load_words
#
# args: none
# rets: none
#
# Load the user specified word list into @words

sub load_words {
    @words = ();

    open( my $FH, "<$words_opt" ) or die "Could not open $words_opt: $!\n";
    while ( my $line = <$FH> ) {
        chomp $line;
        push @words, $line;
    }
    close $FH;

    return;
}

# load_vendors
#
# args: none
# rets: none
#
# Loads vendor mac prefix file into @vendors

sub load_vendors {
    @vendors = ();

    open( my $FH, "<$vendors_opt" ) or die "Could not open $vendors_opt: $!\n";
    while ( my $line = <$FH> ) {
        chomp $line;
        $line =~ /^(\w\w:\w\w:\w\w)/;
        push @vendors, "$1:";
    }
    close $FH;

    return;
}

# gen_essid
#
# args: none
# rets: scalar string $word
#
# Returns a string suitable for use as an ESSID.  Picks it randomly from
# @words

sub gen_essid {
    return $words[ int( rand $#words ) ];
}

# gen_channel
#
# args: none
# rets: scalar int $channel
#
# Returns a number between 1 and $MAX_CHANNEL

sub gen_channel {
    return int( rand $MAX_CHANNEL ) + 1;
}

# gen_power
#
# args: none
# rets: scalar int $channel
#
# Returns a number between 1 and $power_opt or Def if $power_opt is not set

sub gen_power {
    return int( rand $power_opt ) + 1 if $power_opt;
    return "Def";
}

# gen_mac
#
# args: none
# rets: none
#
# Returns a random MAC address with first three octets from @vendors
# last three random.

sub gen_mac {

    return sprintf(
        "%s%02X:%02X:%02X",
        $vendors[ int( rand $#vendors ) ],
        int( rand 256 ),
        int( rand 256 ),
        int( rand 256 )
    );

}

# pick_wep
#
# args: none
# rets: string Y|N
#
# Returns N if wep_opt is not set otherwise returns
# Y with probability $wep_opt

sub pick_wep {
    $wep_opt = 0 if not $wep_opt;

    return "Y" if ( rand(1) < $wep_opt );
    return "N";

}

################################################################
#
# Main
#
print "fakeap 0.3.1 - Wardrivring countermeasures\n";
print "Copyright (c) 2002 Black Alchemy Enterprises. All rights reserved\n\n";

GetOptions(
    "channel=i"   => \$channel_opt,
    "essid=s"     => \$essid_opt,
    "words=s"     => \$words_opt,
    "mac=s"       => \$mac_opt,
    "sleep=s"     => \$sleep_opt,
    "power=i"     => \$power_opt,
    "wep=s"       => \$wep_opt,
    "key=s"       => \$key_opt,
    "interface=s" => \$interface_opt,
    "vendors=s"   => \$vendors_opt
);

usage() and exit if not $interface_opt;
usage() and exit if ( $words_opt and $essid_opt );    # mutually exclusive

print "Using interface $interface_opt:\n";
print "Sleeping $sleep_opt sec\n"             if $sleep_opt;
print "Static channel $channel_opt\n"         if $channel_opt;
print "Static ESSID $essid_opt\n"             if $essid_opt;
print "Static MAC $mac_opt\n"                 if $mac_opt;
print "Generating ESSIDs from $words_opt\n"   if $words_opt;
print "Using WEP with probability $wep_opt\n" if $wep_opt;
print "Using supplied WEP key $key_opt\n"     if $key_opt;
print "Vary Tx power up to $power_opt\n"      if $power_opt;

load_words() if $words_opt;
print "Using $#words words for ESSID generation\n";

load_vendors() if $vendors_opt;
print "Using $#vendors vendors for MAC generation\n";

print
  "-------------------------------------------------------------------------\n";

for ( my $i = 0 ; ; $i++ ) {
    my $essid   = $essid_opt   || gen_essid();
    my $channel = $channel_opt || gen_channel();
    my $mac     = $mac_opt     || gen_mac();
    my $sleep   = $sleep_opt   || 0.25;
    my $wep     = pick_wep();
    my $power   = gen_power();

    if ($wep_opt) {
        system( $CRYPTCONF, "-p", $interface_opt, "ff:ff:ff:ff:ff:ff", "none" )
          if $wep eq "N";
        system( $IWCONFIG, $interface_opt, "key",
            $key_opt ? $key_opt : "s:fakeap", "open" )
          if $wep eq "Y";
    }

   
    system( $IFCONFIG, $interface_opt, "down" );
    system( $IWCONFIG, $interface_opt, "ESSID",   $essid );
    	printf( $IWCONFIG, $interface_opt, "ESSID",   $essid );
    system( $IWCONFIG, $interface_opt, "channel", $channel );
    	printf( $IWCONFIG, $interface_opt, "channel", $channel );
    system( $IFCONFIG, $interface_opt, "hw",      "ether", $mac );
    	printf( $IFCONFIG, $interface_opt, "hw",      "ether", $mac );
    system( $IWCONFIG, $interface_opt, "txpower", $power . "mW" ) if $power_opt;
    	printf( $IWCONFIG, $interface_opt, "txpower", $power . "mW" ) if $power_opt;
    system( $IFCONFIG, $interface_opt, "up" );

    printf( "%i: ESSID=%-15s chan=%02i Pwr=%-3s WEP=%s MAC=%s    \r",
        $i, $essid, $channel, $power, $wep, $mac );

    Time::HiRes::sleep($sleep);
}
```

---

### Post by sjlsam on 2005-06-09
bump

---

### Post by andyeddy525 on 2007-01-14
its a perl script, not a bash script.  try this:

sudo perl ./Desktop/fakeap/fakeap.pl

---

