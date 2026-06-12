---
title: "Evolution Contacts: Import CSV"
date: 2006-12-19
forum: General Help
---

### Post by Deadheded on 2006-12-19
I have a .csv file with names in colum one and email addresses in colum two.  I have two copies of the file one with comma seperated values and one with tab seperated values.  When I go to import either of these files in to Evolution Contacts it puts both the name and email addy in the "full name" field and nothing in the"email address" field.  Anyone have any help or know what field mapping that Evolution is expecting?

---

### Post by aBitLater on 2008-01-08
I have the same problem, a year later... seems like a mapping table should be provided, but I can't find a way to force evolution to give me the option of mapping fields.

aBitLater,

---

### Post by PenguinInAWindowsWorld on 2008-01-11
Guys,
  I was having the same problem importing a csv into evolution.  It worked, but the fields were just a bit off (wrong email addresses, phone number, etc..).

Solution:  Get the source and look at the mappings.

[http://www.gnome.org/projects/evolution/download.shtml]("http://www.gnome.org/projects/evolution/download.shtml") - find the release that matches your version and download the source.

Unzip it.

The file that you want to look at is:
/evolution-<version>/addressbook/importers/evolution-csv-importer.c

Even if you don't have any programming skills you can see what's going on.
"csv_fields_outlook" holds the mappings for an outlook import (as you specified when you ran them import wizard), "csv_fields_mozilla" holds the mozilla mappings and "csv_fields_evolution" holds the evolution mappings.

You can now tweak the CSV file to put the values where you want them.

Cheers.

--PIAWW

---

### Post by aBitLater on 2008-01-13
Thanks... maybe someday I'll be able to recompile evolution after changing the source code mappings to match Outlook :)  That would solve it once and for all, eh?

Thanks for the tip.  

Also, I haven't tried it yet, but I thought it might work: export one contact from Evolution to csv and then compare it with the outlook.csv - then rename the columns for the Outlook csv.

---

### Post by tonywhelan on 2008-02-17
> **aBitLater said:**
> Thanks... maybe someday I'll be able to recompile evolution after changing the source code mappings to match Outlook :)  That would solve it once and for all, eh?

Thanks for the tip.  

Also, I haven't tried it yet, but I thought it might work: export one contact from Evolution to csv and then compare it with the outlook.csv - then rename the columns for the Outlook csv.

Though I like T/Bird I really need my emails to be indexed and Gnome's Tracker won't index T/Bird till they drop their MORK database structure and go to something more sensible. Which may take a year or more - TB3 or TB4 I'd guess.

So today I reinstalled Evolution and all went well except for the address book.

Evolution certainly misplaces or loses data when importing from Thunderbird (whether LDIF, CSV or TXT/TSV). \

There are lots of hints for EVo to TBird export, but not much for going the other way. However, 
I found a perl script which someone wrote in 2005 that maps the fields correctly. I have modified it slightly (so the prompt is in English) but haven't touched the programming code otherwise. It worked nicely for me. 

You need to export your TBird contacts in Tab-Separated-Values format, not CSV or LDIF.  Save the file to your desktop (or wherever you like). Call it whatever (here i'll call it "input").

Save the script as "tsv2vcf" in the same place as you saved the contacts file , make the script executable (right-click, then Properties). Then in a terminal window, change to your desktop directory and execute:
```
perl tsv2vcf input output 
```

This will process the file "input" and creat a vcf file called "output" which you can then import with Evolution's builtin Import facility.

Here is the modified script.
```

#!/usr/bin/perl

#############################################################################
# tsv2vcf takes an address book TSV file as exported by Thunderbird
#         and turns it into a VCF file to be imported as Evolution contacts
# v0.0.2
#
# Copyright (c) 2005 Héctor M. Monacci
# Contact hector@monacci.net
#
# Prompts anglicised 2008 by Tony Whelan
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
Reads an address book file exported from Thunderbird in tab-separated format
and creates a new file in VCF format for importing to Evolution address book.

Virtually any input and output file names are permitted. 
The input file must exist and the script will abort if not found.

Why the need? Because Evolution's built-in import utility does not read 
LDIF/CSV/TXT files correctly; it omits/misfiles some data. 

Script written 2005 by Héctor M. Monacci
This prompt screen anglicised and expanded 2008 by Tony Whelan

Use: $0 input-file output-file
--EndOfUsage
  exit;

}

usage() unless(defined($in) && defined($out));

local( $/, *INFILE ) ;
open (INFILE, $in)
  or die "Unable to open $in: $!\n";

  $contenido_total = <INFILE>;
  close(INFILE);

#

# Eliminamos comillas:
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
# Temp MOD to pull the full name from nickname
# instead of fullname field
# Replace FN line above with the line below
# FN:$_03_Nickname
# end temp MOD Tony W.
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

# Imprimimos el resultado en un archivo VCF:
open (OUTFILE, ">$out")
  or die "Unable to create $out: $!\n";
  print OUTFILE @resultado;
  close(OUTFILE);


```

The original script can be found here: [HTML]https://sourceforge.net/projects/tsv2vcf/[/HTML]

It worked very nicely for me. I even patched it temporarily to pull the "full name" data from the "nickname" field as that's where I had stored people's names in Thunderbird.

My thanks to the original programmer (Hector Monacci) who took the time to make this neat script.

---

### Post by iheartubuntu on 2008-05-20
Many thanks for the help! I extracted the contacts from a MDB file one of my brothers made for my dad years ago and converted it to CSV. Now Im labeling everything correctly before I import into Evolution! I hope it works!



> **PenguinInAWindowsWorld said:**
> Guys,
  I was having the same problem importing a csv into evolution.  It worked, but the fields were just a bit off (wrong email addresses, phone number, etc..).

Solution:  Get the source and look at the mappings.

[http://www.gnome.org/projects/evolution/download.shtml]("http://www.gnome.org/projects/evolution/download.shtml") - find the release that matches your version and download the source.

Unzip it.

The file that you want to look at is:
/evolution-<version>/addressbook/importers/evolution-csv-importer.c

Even if you don't have any programming skills you can see what's going on.
"csv_fields_outlook" holds the mappings for an outlook import (as you specified when you ran them import wizard), "csv_fields_mozilla" holds the mozilla mappings and "csv_fields_evolution" holds the evolution mappings.

You can now tweak the CSV file to put the values where you want them.

Cheers.

--PIAWW

---

