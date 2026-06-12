---
title: "Huge text edit - remove duplicate blocks of text?"
date: 2015-04-23
forum: General Help
---

### Post by insil on 2015-04-23
I'm working with a huge text file >3GB, and it has duplicate blocks  of text that I need removed, leaving only the first copy of the said  text block.  Is there an easy way to do this?  I've googled about sed,  but can't figure out the right commands.

The blocks of text that I work with all start with a number and end with  $$$$, and I would want the whole thing removed if duplicated, starting  with that number and ending with $$$$, but not if anything else is same but the number in the beginning is different.  Here's what a typical entry from  my file (chemical description data, in case you wondered [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG] ) looks like--I have over 500K of these in my file, but likely thousands of duplicates.

> 56642968
  -OEChem-04211509202D

 38 37  0     0  0  0  0  0  0999 V2000
    3.7320    4.5000    0.0000 K   0  3  0  0  0  0  0  0  0  0  0  0
    3.7320    1.5000    0.0000 S   0  0  0  0  0  0  0  0  0  0  0  0
    4.5981    4.0000    0.0000 O   0  5  0  0  0  0  0  0  0  0  0  0
    4.7320    1.5000    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    2.7320    1.5000    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
    3.7320    2.5000    0.0000 N   0  0  0  0  0  0  0  0  0  0  0  0
    3.7320   -2.5000    0.0000 N   0  0  0  0  0  0  0  0  0  0  0  0
    2.8660   -4.0000    0.0000 N   0  0  0  0  0  0  0  0  0  0  0  0
    2.8660   -3.0000    0.0000 N   0  0  0  0  0  0  0  0  0  0  0  0
    5.4641    2.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    6.3301    3.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    3.7320    0.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    4.5981    3.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.8660    0.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    4.5981    0.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    7.1962    2.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    3.7320   -1.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.8660   -1.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    4.5981   -1.0000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    2.0000   -4.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    3.7320   -4.5000    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0
    5.0656    2.0250    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    5.8626    2.0250    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    6.7287    3.4750    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    5.9316    3.4750    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    2.3291    0.3100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    5.1350    0.3100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    6.8862    1.9631    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    7.7331    2.1900    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    7.5062    3.0369    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    2.3291   -1.3100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    5.1350   -1.3100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    1.6900   -3.9631    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    1.4631   -4.8100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    3.4220   -5.0369    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    4.2690   -4.8100    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    4.0420   -3.9631    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    2.3100   -5.0369    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
  2  4  2  0  0  0  0
  2  5  2  0  0  0  0
  2  6  1  0  0  0  0
  2 12  1  0  0  0  0
  3 13  1  0  0  0  0
  6 13  2  0  0  0  0
  7  9  2  0  0  0  0
  7 17  1  0  0  0  0
  8  9  1  0  0  0  0
  8 20  1  0  0  0  0
  8 21  1  0  0  0  0
 10 11  1  0  0  0  0
 10 13  1  0  0  0  0
 10 22  1  0  0  0  0
 10 23  1  0  0  0  0
 11 16  1  0  0  0  0
 11 24  1  0  0  0  0
 11 25  1  0  0  0  0
 12 14  2  0  0  0  0
 12 15  1  0  0  0  0
 14 18  1  0  0  0  0
 14 26  1  0  0  0  0
 15 19  2  0  0  0  0
 15 27  1  0  0  0  0
 16 28  1  0  0  0  0
 16 29  1  0  0  0  0
 16 30  1  0  0  0  0
 17 18  2  0  0  0  0
 17 19  1  0  0  0  0
 18 31  1  0  0  0  0
 19 32  1  0  0  0  0
 20 33  1  0  0  0  0
 20 34  1  0  0  0  0
 20 38  1  0  0  0  0
 21 35  1  0  0  0  0
 21 36  1  0  0  0  0
 21 37  1  0  0  0  0
M  CHG  2   1   1   3  -1
M  END
> <PUBCHEM_COMPOUND_CID>
56642968

> <PUBCHEM_COMPOUND_CANONICALIZED>
1

> <PUBCHEM_CACTVS_COMPLEXITY>
452

> <PUBCHEM_CACTVS_HBOND_ACCEPTOR>
7

> <PUBCHEM_CACTVS_HBOND_DONOR>
0

> <PUBCHEM_CACTVS_ROTATABLE_BOND>
6

> <PUBCHEM_CACTVS_SUBSKEYS>
AAADceBzsABAQAAAAAAAAAAAAAAAAAAAAAAwAAAAAAAAAAABAA   AAHgQIQAAACAiB0AQywYIAAAKiACRiQHDCABAgAgAIiBg4ZIgI   ICKAkZGAIABkgAAIyAcQAAAAAAQAAAAAAAAACAAAAAAAAAAAAA  AAAA==

> <PUBCHEM_IUPAC_OPENEYE_NAME>
potassium;(1E)-N-[4-(dimethylaminoazo)phenyl]sulfonylbutanimidate

> <PUBCHEM_IUPAC_CAS_NAME>
potassium;(1E)-N-[4-(dimethylaminoazo)phenyl]sulfonylbutanimidate

> <PUBCHEM_IUPAC_NAME>
potassium;(1E)-N-[4-(dimethylaminodiazenyl)phenyl]sulfonylbutanimidate

> <PUBCHEM_IUPAC_SYSTEMATIC_NAME>
potassium;(1E)-N-[4-(dimethylaminodiazenyl)phenyl]sulfonylbutanimidate

> <PUBCHEM_IUPAC_TRADITIONAL_NAME>
potassium;(1E)-N-[4-(dimethylaminoazo)phenyl]sulfonylbutyrimidate

> <PUBCHEM_IUPAC_INCHI>
InChI=1S/C12H18N4O3S.K/c1-4-5-12(17)14-20(18,19)11-8-6-10(7-9-11)13-15-16(2)3;/h6-9H,4-5H2,1-3H3,(H,14,17);/q;+1/p-1

> <PUBCHEM_IUPAC_INCHIKEY>
HPLXIKKNZAPAJN-UHFFFAOYSA-M

> <PUBCHEM_EXACT_MASS>
336.065843

> <PUBCHEM_MOLECULAR_FORMULA>
C12H17KN4O3S

> <PUBCHEM_MOLECULAR_WEIGHT>
336.45168

> <PUBCHEM_OPENEYE_CAN_SMILES>
CCCC(=NS(=O)(=O)C1=CC=C(C=C1)N=NN(C)C)[O-].[K+]

> <PUBCHEM_OPENEYE_ISO_SMILES>
CCC/C(=N\S(=O)(=O)C1=CC=C(C=C1)N=NN(C)C)/[O-].[K+]

> <PUBCHEM_CACTVS_TPSA>
106

> <PUBCHEM_MONOISOTOPIC_WEIGHT>
336.065843

> <PUBCHEM_TOTAL_CHARGE>
0

> <PUBCHEM_HEAVY_ATOM_COUNT>
21

> <PUBCHEM_ATOM_DEF_STEREO_COUNT>
0

> <PUBCHEM_ATOM_UDEF_STEREO_COUNT>
0

> <PUBCHEM_BOND_DEF_STEREO_COUNT>
1

> <PUBCHEM_BOND_UDEF_STEREO_COUNT>
0

> <PUBCHEM_ISOTOPIC_ATOM_COUNT>
0

> <PUBCHEM_COMPONENT_COUNT>
2

> <PUBCHEM_CACTVS_TAUTO_COUNT>
1

> <PUBCHEM_NONSTANDARDBOND>
1  3  7

> <PUBCHEM_COORDINATE_TYPE>
1
5
255

> <PUBCHEM_BONDANNOTATIONS>
12  14  8
12  15  8
14  18  8
15  19  8
17  18  8
17  19  8

$$$$

---

### Post by dino99 on 2015-04-23
you might find some ideas with that old thread  [http://ubuntuforums.org/showthread.php?t=1647104](http://ubuntuforums.org/showthread.php?t=1647104)
and gedit also have features [https://yaserxp.wordpress.com/2008/09/03/5-must-have-gedit-plugins-for-programmers/](https://yaserxp.wordpress.com/2008/09/03/5-must-have-gedit-plugins-for-programmers/)

---

### Post by dragonfly41 on 2015-04-24
My guess is that you will have to use a concordance analysis tool which can work on such a large corpus.

[http://mgto.org/free-concordance-keyword-frequency-text-analysis-tools/](http://mgto.org/free-concordance-keyword-frequency-text-analysis-tools/)

I have used TextSTAT for such analysis.  I suggest that you try it.

[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

Download the python source code (note that TextSTAT will NOT work with python 3.0 so use python 2.7).

[http://neon.niederlandistik.fu-berlin.de/static/textstat/TextSTAT-2.9c-source.zip](http://neon.niederlandistik.fu-berlin.de/static/textstat/TextSTAT-2.9c-source.zip)

Unzip into some user folder .. say .. ~/TextSTAT

read quickstart_textstat.pdf

Launch command terminal in that directory.

cd ~/TextSTAT

Run command .. python TextSTAT.pyw

Create your text corpus (you can build up a manifest of multiple text files).

Run Concordance test to inspect duplicates of text patterns. Run a filter.

If TextSTAT does not meet your needs refer to [http://www.kdnuggets.com](http://www.kdnuggets.com) for other text analysis tools.

---

