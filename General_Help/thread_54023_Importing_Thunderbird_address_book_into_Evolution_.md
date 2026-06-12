---
title: "Importing Thunderbird address book into Evolution contacts"
date: 2005-08-03
forum: General Help
---

### Post by etitor on 2005-08-03
It's more than half a year now since I first installed Ubuntu to replace my Mandrake. I won't look back. But Mandrake's heritage included, in my case, using Thunderbird as email client.

Last week I began playing with Evolution and I just want to give it a try.

After some googleing I think there is no ready-made way to import Thunderbird's address book into Evolution contacts (LDIF exports from Thunderbird seem to be incompletely imported into Evolution). Pending the great moment when I get to manage LDAP stuff, I want to keep all my email mboxes and all my address book information when I make the change to Evolution.

I plan to build this week a short Perl program that would take Thundebird's address book (exported from Thunderbird in TSV form) and transform it into a VCF file ready to be imported into Evolution.

More news soon, I promise. If your are interested, keep an eye here. If you know for sure this has already been done, please let me know ASAP (and show me where)!

---

### Post by matthew on 2005-08-03
It's kind of a workaround solution, but you could import the csv file into the Mozilla suite (which you would have to install briefly) and then import the Mozilla filetype (forget what it's called) into Evolution. Should work for you. That is what I did when I migrated from Outlook on Windows to Evolution on Ubuntu.

---

### Post by etitor on 2005-08-04
Thank you Matthew.

Last night Perl was definitely on my side and I managed to create a working alpha of what I will call tsv2vcf.

I just need to tweak two or three aesthetical bugs to release it. GPL of course.

I think I will hang the program in Sourceforge and paste a link here. Or can Perl scripts be attached here at Ubuntuforums?

---

### Post by alegomes on 2005-08-04
Did you get yout Thunderbird folders and messades into Evolution ?

Did you finished your tsv2vcf script ?

thanks

---

### Post by etitor on 2005-08-04
alegomes:

Yes I could import all my folders and messages into Evolution.

Yes I wrote the perl script (tsv2vcf, soon in Sourceforge). It isn't finished yet, but it works. I'd say it's 80% ready now.

I started this thread only yesterday! I plan to release tsv2vcf, as I said in my first post, this week.

---

### Post by matthew on 2005-08-04
[QUOTE=etitor]Thank you Matthew.

Last night Perl was definitely on my side and I managed to create a working alpha of what I will call tsv2vcf.

I just need to tweak two or three aesthetical bugs to release it. GPL of course.

I think I will hang the program in Sourceforge and paste a link here. Or can Perl scripts be attached here at Ubuntuforums?[/QUOTE]

I'll look forward to seeing it. There have been a lot of us that have done silly workarounds like what I described earlier. You will be making a lot of people's lives easier. Thanks!

---

### Post by etitor on 2005-08-04
Matthew,

Look forward no more. Please visit [https://sourceforge.net/projects/tsv2vcf/](https://sourceforge.net/projects/tsv2vcf/) and download my script.

Hope it works for you. It does for me.

---

### Post by matthew on 2005-08-05
Sweet! I am moving this weekend and things will be a mess over the next week or so so I'll take a look then. On behalf of the community, thanks!

---

### Post by fabcargo on 2006-06-16
Thanks for the script. I am a noob so I dont know how to run it. Please kindly advise how to run it. I would like to import my thunderbird address book to evolution.

thanks!

---

### Post by Thies on 2006-07-24
Same "problem" here ... I have no clue how to handle the script. Maybe some one with Perl knowledge (if not the author himself) could enlighten us how to convert the tsv book to the cvf contacts. Thanks!
I guess it's somewhere in the beginning of the script [sub usage ?!?]? 

[PHP]
#!/usr/bin/perl

#############################################################################
# tsv2vcf takes an address book TSV file as exported by Thunderbird
#         and turns it into a VCF file to be imported as Evolution contacts
# v0.0.2
#
# Copyright (c) 2005 Héctor M. Monacci
# Contact hector@monacci.net
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#
#############################################################################

use strict;
#use warnings;
#use diagnostics;
use locale;
use Encode;

my $contenido_total;
my @renglones;

my $in  = $ARGV[0];
my $out = $ARGV[1];

sub usage
{
  print STDERR << "--EndOfUsage";

Convierte una lista en formato TSV (valores separados por tabulaciones),
tal como la que produce Thunderbird al exportar su libreta de direcciones,
en una lista en formato vCard adecuada para ser importada en Evolution.

Uso: $0 [archivo.tsv archivo.vcf]

--EndOfUsage



  exit;

}



usage() unless(defined($in) && defined($out));





local( $/, *INFILE ) ;

open (INFILE, $in)

  or die "Imposible abrir $in: $!\n";

  $contenido_total = <INFILE>;

  close(INFILE);







#

# Eliminamos comillas:

#

$contenido_total =~ s/"//g;







# 

# Cargamos en un array:

#

@renglones = split(/\n/, $contenido_total);







#

# Asignamos a los campos:

#

  my $este;

  my @resultado;



  foreach (@renglones) {

    my @rengloncitos = split(/\t/, $_);

    my $_00_First_Name           = $rengloncitos[ 0];

    my $_01_Last_Name            = $rengloncitos[ 1];

    my $_02_Screen_Name          = $rengloncitos[ 2];

    my $_03_Nickname             = $rengloncitos[ 3];

    my $_04_Email_Address        = $rengloncitos[ 4];

    my $_05_Email_2_Address      = $rengloncitos[ 5];

    my $_06_Business_Phone       = $rengloncitos[ 6];

    my $_07_Home_Phone           = $rengloncitos[ 7];

    my $_08_Business_Fax         = $rengloncitos[ 8];

    my $_09_Pager                = $rengloncitos[ 9];

    my $_10_Mobile_Phone         = $rengloncitos[10];

    my $_11_Home_Street          = $rengloncitos[11];

    my $_12_Home_Street_2        = $rengloncitos[12];

    my $_13_Home_City            = $rengloncitos[13];

    my $_14_Home_State           = $rengloncitos[14];

    my $_15_Home_Postal_Code     = $rengloncitos[15];

    my $_16_Home_Country         = $rengloncitos[16];

    my $_17_Business_Street      = $rengloncitos[17];

    my $_18_Business_Street_2    = $rengloncitos[18];

    my $_19_Business_City        = $rengloncitos[19];

    my $_20_Business_State       = $rengloncitos[20];

    my $_21_Business_Postal_Code = $rengloncitos[21];

    my $_22_Business_Country     = $rengloncitos[22];

    my $_23_Title                = $rengloncitos[23];

    my $_24_Department           = $rengloncitos[24];

    my $_25_Organization         = $rengloncitos[25];

    my $_26_Business_Web         = $rengloncitos[26];

    my $_27_Web_Page             = $rengloncitos[27];

    my $_28_s                    = $rengloncitos[28];

    my $_29_t                    = $rengloncitos[29];

    my $_30_u                    = $rengloncitos[30];

    my $_31_v                    = $rengloncitos[31];

    my $_32_w                    = $rengloncitos[32];

    my $_33_x                    = $rengloncitos[33];

    my $_34_y                    = $rengloncitos[34];

    my $_35_Notes                = $rengloncitos[35];

    my $_36_z                    = $rengloncitos[36];



	my $plantilla = "BEGIN:VCARD

VERSION:3.0

URL:$_27_Web_Page

TITLE:$_23_Title

ORG:$_25_Organization;$_24_Department;

NICKNAME:$_03_Nickname

NOTE:$_35_Notes

FN:$_00_First_Name $_01_Last_Name

N:$_01_Last_Name;$_00_First_Name;;;

X-EVOLUTION-FILE-AS:$_01_Last_Name, $_00_First_Name

X-MOZILLA-HTML:TRUE

EMAIL;TYPE=HOME:$_04_Email_Address

EMAIL;TYPE=WORK:$_05_Email_2_Address

TEL;TYPE=WORK;TYPE=VOICE:$_06_Business_Phone

TEL;TYPE=HOME;TYPE=VOICE:$_07_Home_Phone

TEL;TYPE=CELL:$_10_Mobile_Phone

TEL;TYPE=WORK;TYPE=FAX:$_08_Business_Fax

TEL;TYPE=PAGER:$_09_Pager

ADR;TYPE=WORK:;;$_17_Business_Street $_18_Business_Street_2;$_19_Business_City;$_20_Business_State;$_21_Business_Postal_Code;$_22_Business_Country

LABEL;TYPE=WORK:$_17_Business_Street $_18_Business_Street_2\\n$_21_Business_Postal_Code $_19_Business_City, $_20_Business_State\\n$_22_Business_Country

ADR;TYPE=HOME:;;$_11_Home_Street $_12_Home_Street_2;$_13_Home_City;$_14_Home_State;$_15_Home_Postal_Code;$_16_Home_Country

LABEL;TYPE=HOME:$_11_Home_Street $_12_Home_Street_2\\n$_15_Home_Postal_Code $_13_Home_City, $_14_Home_State\\n$_16_Home_Country

END:VCARD



";



#

# Correcciones particulares:

#

    $plantilla =~ s/,/\\,/g;

	$plantilla =~ s/\\,\s$//g;

	$plantilla =~ s/: \\n \\, \\n/:/g;

	$plantilla =~ s/\\, \\n/\\n/g;

	$plantilla =~ s/\\, \n/\n/g;

	$plantilla =~ s/:;; ;;;;/:/g;

	$plantilla =~ s/.*\:\n//g;



    push (@resultado, $plantilla);

}







#

# Imprimimos el resultado en un archivo VCF:

#

open (OUTFILE, ">$out")

  or die "Imposible abrir $out: $!\n";

  print OUTFILE @resultado;

  close(OUTFILE);



[/PHP]

---

