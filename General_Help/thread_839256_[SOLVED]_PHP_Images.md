---
title: "[SOLVED] PHP Images"
date: 2008-06-24
forum: General Help
---

### Post by CrusaderAD on 2008-06-24
I need to display images on a template. It displays the names but not the image. Here is the code:


<?
// Strip out all html in description for short descriptions
$description = strip_tags($row[description], '');

// Now limit the processed description tag to only 200 characters
$description2=substr($description, 0, 200);
?>

<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>
<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href="product.php?skew=<? echo $row[skew]; ?>">
<img src="http://www.evitamins.com/images/products/",""<? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>
</TD>
<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href="product.php?skew=<? echo $row[skew]; ?>"><? echo $row[name]; ?></A><br>
Made By: <a href="brand.php?brandname=<? echo $row[brand]; ?>"><? echo $row[brand]; ?></A><br>
$<? echo $row[our_price]; ?> for <? echo $row[package_type]; ?><br>
<? echo $description2; ?>... <a href="product.php?skew=<? echo $row[skew]; ?>">More Info >>></A>
</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>


What am I missing?

---

### Post by cpetercarter on 2008-06-24
There is a strange comma "," in the middle of the image tag; the ampersands in the img tag should be url encoded (&amp;); there is no closure to the image tag ( />). maybe its one of those.

PS Sorry about the smiley above. It seems that if you type & a m p ; it happens automatically (&amp;) - see what I mean!

---

### Post by CrusaderAD on 2008-06-24
> **cpetercarter said:**
> There is a strange comma "," in the middle of the image tag; the ampersands in the img tag should be url encoded (&amp;); there is no closure to the image tag ( />). maybe its one of those.

PS Sorry about the smiley above. It seems that if you type & a m p ; it happens automatically (&amp;) - see what I mean!
I changed it to:

<img src="http://www.evitamins.com/images/products/"<? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>

Same result.

---

### Post by CrusaderAD on 2008-06-24
> **cpetercarter said:**
> There is a strange comma "," in the middle of the image tag; the ampersands in the img tag should be url encoded (&amp;); there is no closure to the image tag ( />). maybe its one of those.

PS Sorry about the smiley above. It seems that if you type & a m p ; it happens automatically (&amp;) - see what I mean!
Then I changed it to:

<img src="http://www.evitamins.com/images/products/"/><? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>

Now it displays the link:

http://www.evitamins.com/images/products/NPacidophilus.jpg&sharpenvalue=&Rotate=0" border="0" alt="Acidophilus" align="left">

---

### Post by cpetercarter on 2008-06-24
Is that the link you want to display? Or is there still aproblem?

---

### Post by CrusaderAD on 2008-06-24
No, I want to display the image, not a link.

---

### Post by Gunman1982 on 2008-06-24
> **raptormanad said:**
> Then I changed it to:

<img src="http://www.evitamins.com/images/products/"/><? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>

Now it displays the link:

http://www.evitamins.com/images/products/NPacidophilus.jpg&sharpenvalue=&Rotate=0" border="0" alt="Acidophilus" align="left">

try to stick the php code into the "" ... like: 
```
<img src="http://www.evitamins.com/images/products/<? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>
```

that should work more likely

---

### Post by CrusaderAD on 2008-06-24
> **Gunman1982 said:**
> try to stick the php code into the "" ... like: 
```
<img src="http://www.evitamins.com/images/products/<? echo $row[image]; ?>&sharpenvalue=&Rotate=0" border="0" alt="<? echo $row[name]; ?>" align="left"></A>
```

that should work more likely
Now it just displays the Name, no link, no image.

---

### Post by Gunman1982 on 2008-06-24
Can you show what the html code is for that specific place.

---

### Post by CrusaderAD on 2008-06-24
Here's the page that has the include script in it, including the previous script I posted:


<?
include("config.php");

// Get Category Name Below For SE Optimizing

$cid = (isset($_REQUEST['cid'])) ? $_REQUEST['cid']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;
$category = (isset($_GET['category'])) ? $_GET['category'] : null;

$sql = "SELECT catname
	    FROM categories
	    WHERE cid = '$cid'
	";
$query = mysql_query($sql);
$category = mysql_fetch_array($query);
?>
<html>
<head>
<title><? echo $category[0]; ?> Vitamins & Supplements</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<META NAME="description" CONTENT="<? echo $category[0]; ?> health vitamins and supplements.">
<META NAME="keywords" CONTENT="<? echo $category[0]; ?>,buy <? echo $category[0]; ?>">
<meta name="Language" content="en">
<meta name="Distribution" content="global">
<meta name="author" content="<? echo $category[0]; ?>">
<META NAME="robots" CONTENT="index,follow">

<? include("style.php"); ?>

</head>

<body topmargin="15" bgcolor=#ffffff>

<H1 align=center><? echo $category[0]; ?></H1>
<H2 align=center><? echo $category[0]; ?> Supplements & Vitamins</H2>

<!---Top Stuff--->
<table border=0 width=98% cellpadding=5 cellspacing=0 align=center bgcolor=#ffffff>
<TR>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<? include("categories-drop-down.php"); ?>
</TD>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<? include("brands-drop-down.php"); ?>
</TD>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<? include("search-box.php"); ?>
</TD>
</TR></Table>
<!---Top Stuff--->

<!---Content Stuff--->
<table border=0 width=98% cellpadding=5 cellspacing=0 align=center bgcolor=#ffffff>
<TR>
<TD align=left width=15% bgcolor=#ffffff valign=top>
<b>By Category</b><br><br>
<? include("categories-listed.php"); ?>
</TD>
<TD align=left width=70% bgcolor=#ffffff valign=top>

<b><? echo $category[0]; ?> Health & Vitamin Supplements</b><br><br>

<?
if(!$start){
$start = 0;
}
if(!$limit){
$limit = 10;
}
$end=($start+$limit);

$sql = "SELECT *
	    FROM evitamins_products
        WHERE category='$cid'
	   ";
if(mysql_num_rows(mysql_query($sql)) < 1){
echo "Error!";
}

// Get Products Within The Category Below
$result = mysql_query("select * from evitamins_products WHERE category='$cid' ORDER by name ASC LIMIT $start, $limit") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
include("show-thumbnail.php");
}

$prv = ($start-$limit);
$nxt = ($start+$limit);
if($prv < 0){
$previous = "";
}else {
$previous = "<a href=\"category.php?cid=$cid&start=$prv&limit=$limit\"><<< Previous $limit $category[0] Products</a>";
}
if(mysql_num_rows(mysql_query($sql)) < $nxt){
$next = "";
}else {
$next = "<a href=\"category.php?cid=$cid&start=$nxt&limit=$limit\">Next $limit $category[0] Products >>></a>";
}
if(mysql_num_rows(mysql_query($sql)) > $limit){
echo "
<P><table border=1 bordercolor=#000000 align=center width=100% bgcolor=#ffffff cellpadding=3 cellspacing=0><TR>
<TD align=center>
<b>$previous</b> &nbsp; &nbsp; &nbsp; <b>$next</b>
</font></TR></TD></table><P>
";
}

mysql_free_result($result);
?>

</TD>
<TD align=left width=15% bgcolor=#ffffff valign=top>
<b><font color=#CC0000><u>Current Specials</u></font></b><br><br>
<? include("current-specials.php"); ?>
</TD>
</TR></Table>
<!---Content Stuff--->

<? include("bottom.php"); ?>

</body>
</html>

---

### Post by CrusaderAD on 2008-06-24
The file I'm trying to get to work is the show-thumbnail.php

---

### Post by Gunman1982 on 2008-06-24
what I meant is, what is really shown as html, if you say just the name is shown in the browser than its still hard to conclude to the actual html code. Open the page, right click on the page -> 'View Page Source' and look whats really send to your browser from the server.

---

### Post by CrusaderAD on 2008-06-24
Here's the source:


<html>
<head>
<title>Vitamins & Supplements Made By AchievOne</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<META NAME="description" CONTENT="AchievOne health vitamins and supplements.">
<META NAME="keywords" CONTENT="AchievOne">
<meta name="Language" content="en">
<meta name="Distribution" content="global">
<meta name="author" content="AchievOne">
<META NAME="robots" CONTENT="index,follow">

<style type="text/css">
	body,td			{ font-family: Arial, Helvetica, sans-serif; color: #000000; font-size: 11px; }
	A:link			{ text-decoration: underline; color: #000099; }
	A:visited		{ text-decoration: underline; color: #000099; }
	A:hover			{ text-decoration: underline; color: #000000; }
</style>
</head>

<body topmargin="15" bgcolor=#ffffff>

<H1 align=center>Vitamins & Supplements Made By AchievOne</H1>
<H2 align=center>AchievOne Supplements & Vitamins</H2>

<!---Top Stuff--->
<table border=0 width=98% cellpadding=5 cellspacing=0 align=center bgcolor=#ffffff>
<TR>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<form method="post" action="category.php">
<select name=cid>
<OPTION value="0">Shop By Category</OPTION>

<OPTION value="91">Acidophilus</OPTION>

<OPTION value="77">Allergy</OPTION>

<OPTION value="49">Amino Acids</OPTION>

<OPTION value="3">Antioxidants</OPTION>

<OPTION value="92">Anxiety</OPTION>

<OPTION value="4">Arthritis - Joints</OPTION>

<OPTION value="103">Bars</OPTION>

<OPTION value="5">Blood Pressure</OPTION>

<OPTION value="6">Bones</OPTION>

<OPTION value="104">Books</OPTION>

<OPTION value="7">Brain - Memory</OPTION>

<OPTION value="8">Cancer</OPTION>

<OPTION value="9">Childrens</OPTION>

<OPTION value="10">Cholesterol</OPTION>

<OPTION value="11">Circulation</OPTION>

<OPTION value="12">Cold - Flu</OPTION>

<OPTION value="90">Colon</OPTION>

<OPTION value="30">Depression</OPTION>

<OPTION value="13">Detox</OPTION>

<OPTION value="14">Diabetes</OPTION>

<OPTION value="71">Diets</OPTION>

<OPTION value="47">Digestion</OPTION>

<OPTION value="15">Energy</OPTION>

<OPTION value="75">Facial Care</OPTION>

<OPTION value="88">Glandulars</OPTION>

<OPTION value="94">Green Foods</OPTION>

<OPTION value="96">Growth Hormones</OPTION>

<OPTION value="74">Hair Care</OPTION>

<OPTION value="95">Hangover</OPTION>

<OPTION value="50">Headaches</OPTION>

<OPTION value="87">Hearing - Ears</OPTION>

<OPTION value="17">Heart Support</OPTION>

<OPTION value="62">Herbs</OPTION>

<OPTION value="60">Immune System</OPTION>

<OPTION value="25">Kidney - Bladder</OPTION>

<OPTION value="19">Liver</OPTION>

<OPTION value="73">Lotions - Creams</OPTION>

<OPTION value="105">Low Carb</OPTION>

<OPTION value="31">Lungs</OPTION>

<OPTION value="23">Menopause</OPTION>

<OPTION value="20">Mens Health</OPTION>

<OPTION value="29">Minerals</OPTION>

<OPTION value="63">Miscellaneous</OPTION>

<OPTION value="101">Mouth Care</OPTION>

<OPTION value="76">Nail Care</OPTION>

<OPTION value="97">Noni</OPTION>

<OPTION value="65">Oils</OPTION>

<OPTION value="85">Pain Relievers</OPTION>

<OPTION value="78">Personal Care</OPTION>

<OPTION value="100">Pet Care</OPTION>

<OPTION value="22">PMS</OPTION>

<OPTION value="102">Proteins</OPTION>

<OPTION value="21">Rest & Relax</OPTION>

<OPTION value="51">Sexual Help</OPTION>

<OPTION value="16">Skin Care</OPTION>

<OPTION value="99">Smoking</OPTION>

<OPTION value="32">Sports Nutrition</OPTION>

<OPTION value="24">Stress</OPTION>

<OPTION value="93">Teenagers Health</OPTION>

<OPTION value="33">Vision</OPTION>

<OPTION value="52">Vitamin A</OPTION>

<OPTION value="53">Vitamin B</OPTION>

<OPTION value="54">Vitamin C</OPTION>

<OPTION value="55">Vitamin D</OPTION>

<OPTION value="56">Vitamin E</OPTION>

<OPTION value="89">Vitamin K</OPTION>

<OPTION value="57">Vitamin Multiple</OPTION>

<OPTION value="27">Weight Loss</OPTION>

<OPTION value="26">Womens Health</OPTION>
</select>
<input type="submit" value=" GO ">
</form></TD>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<form method="post" action="brand.php">

<select name="brandname">
<OPTION value="0">Shop By Brand</OPTION>

<OPTION value="4 Your Health">4 Your Health</OPTION>

<OPTION value="4everPets">4everPets</OPTION>

<OPTION value="Abkit">Abkit</OPTION>

<OPTION value="Abra Therapeutic">Abra Therapeutic</OPTION>

<OPTION value="Absolute Nutrition">Absolute Nutrition</OPTION>

<OPTION value="Absorbaid">Absorbaid</OPTION>

<OPTION value="Abundance Marketing">Abundance Marketing</OPTION>

<OPTION value="Accu Fitness">Accu Fitness</OPTION>

<OPTION value="AchievOne">AchievOne</OPTION>

<OPTION value="Action Labs">Action Labs</OPTION>

<OPTION value="ActiPet">ActiPet</OPTION>

<OPTION value="Adams Respiratory Therapeutics">Adams Respiratory Therapeutics</OPTION>

<OPTION value="Advanced Muscle Science">Advanced Muscle Science</OPTION>

<OPTION value="Advanced Sports Nutrition">Advanced Sports Nutrition</OPTION>

<OPTION value="Agape Health Products">Agape Health Products</OPTION>

<OPTION value="Alacer Corporation">Alacer Corporation</OPTION>

<OPTION value="Alba Botanica">Alba Botanica</OPTION>

<OPTION value="All Terrain">All Terrain</OPTION>

<OPTION value="AlliMax">AlliMax</OPTION>

<OPTION value="ALR Industries">ALR Industries</OPTION>

<OPTION value="Alta Health Products">Alta Health Products</OPTION>

<OPTION value="Alvita">Alvita</OPTION>

<OPTION value="Amazing Herbs">Amazing Herbs</OPTION>

<OPTION value="American Biologics">American Biologics</OPTION>

<OPTION value="American BioSciences">American BioSciences</OPTION>

<OPTION value="American Biotech Labs">American Biotech Labs</OPTION>

<OPTION value="American Health">American Health</OPTION>

<OPTION value="Amerifit">Amerifit</OPTION>

<OPTION value="Amino Vital">Amino Vital</OPTION>

<OPTION value="Anabolic Xtreme">Anabolic Xtreme</OPTION>

<OPTION value="Aoqili">Aoqili</OPTION>

<OPTION value="Applied Nutrition">Applied Nutrition</OPTION>

<OPTION value="Aqua Flora">Aqua Flora</OPTION>

<OPTION value="Arizona Natural">Arizona Natural</OPTION>

<OPTION value="Ark Naturals">Ark Naturals</OPTION>

<OPTION value="Artemis Woman">Artemis Woman</OPTION>

<OPTION value="AST Sports Science">AST Sports Science</OPTION>

<OPTION value="At Last, Inc.">At Last, Inc.</OPTION>

<OPTION value="Atkins">Atkins</OPTION>

<OPTION value="Aura Cacia">Aura Cacia</OPTION>

<OPTION value="Avalon Organics">Avalon Organics</OPTION>

<OPTION value="Axis Labs">Axis Labs</OPTION>

<OPTION value="Ayurceutics">Ayurceutics</OPTION>

<OPTION value="Azure Cosmeceuticals">Azure Cosmeceuticals</OPTION>

<OPTION value="Baby's Bliss">Baby's Bliss</OPTION>

<OPTION value="Bach Flower Remedies">Bach Flower Remedies</OPTION>

<OPTION value="Barmensen Labs">Barmensen Labs</OPTION>

<OPTION value="Baywood">Baywood</OPTION>

<OPTION value="Beano">Beano</OPTION>

<OPTION value="Beauty Without Cruelty">Beauty Without Cruelty</OPTION>

<OPTION value="Bella Lucy">Bella Lucy</OPTION>

<OPTION value="Berkeley Premium Nutraceuticals">Berkeley Premium Nutraceuticals</OPTION>

<OPTION value="Better Health">Better Health</OPTION>

<OPTION value="Bhelliom Enterprises">Bhelliom Enterprises</OPTION>

<OPTION value="Bio-Form Essentials">Bio-Form Essentials</OPTION>

<OPTION value="Bio-Strath">Bio-Strath</OPTION>

<OPTION value="Bio-Tech">Bio-Tech</OPTION>

<OPTION value="Biochem Sports">Biochem Sports</OPTION>

<OPTION value="Bioforce">Bioforce</OPTION>

<OPTION value="Biomed Comm">Biomed Comm</OPTION>

<OPTION value="BioNutraceuticals">BioNutraceuticals</OPTION>

<OPTION value="BioNutritional Research Group">BioNutritional Research Group</OPTION>

<OPTION value="BioQuest">BioQuest</OPTION>

<OPTION value="Biosential">Biosential</OPTION>

<OPTION value="Biotec">Biotec</OPTION>

<OPTION value="Biotest Laboratories">Biotest Laboratories</OPTION>

<OPTION value="Biotics Research Corp.">Biotics Research Corp.</OPTION>

<OPTION value="Bliss by Mom">Bliss by Mom</OPTION>

<OPTION value="Blue Spring">Blue Spring</OPTION>

<OPTION value="BNG Enterprises">BNG Enterprises</OPTION>

<OPTION value="Boericke and Tafel">Boericke and Tafel</OPTION>

<OPTION value="Boiron">Boiron</OPTION>

<OPTION value="Boland Naturals">Boland Naturals</OPTION>

<OPTION value="Books on Health">Books on Health</OPTION>

<OPTION value="Botanical Solutions">Botanical Solutions</OPTION>

<OPTION value="Broadmoore Labs">Broadmoore Labs</OPTION>

<OPTION value="Bronner">Bronner</OPTION>

<OPTION value="BSN">BSN</OPTION>

<OPTION value="Buried Treasure">Buried Treasure</OPTION>

<OPTION value="Burt's Bees">Burt's Bees</OPTION>

<OPTION value="Canker Sores Begone">Canker Sores Begone</OPTION>

<OPTION value="Carb-Boom">Carb-Boom</OPTION>

<OPTION value="Cardio Fire">Cardio Fire</OPTION>

<OPTION value="Carlson Labs">Carlson Labs</OPTION>

<OPTION value="Carter-Reed">Carter-Reed</OPTION>

<OPTION value="Castiva">Castiva</OPTION>

<OPTION value="Celestial Seasonings">Celestial Seasonings</OPTION>

<OPTION value="Central Coast Nutraceuticals">Central Coast Nutraceuticals</OPTION>

<OPTION value="Cerburg">Cerburg</OPTION>

<OPTION value="Champion Nutrition">Champion Nutrition</OPTION>

<OPTION value="Chandrika">Chandrika</OPTION>

<OPTION value="Chaser">Chaser</OPTION>

<OPTION value="ChildLife">ChildLife</OPTION>

<OPTION value="China Mystique">China Mystique</OPTION>

<OPTION value="CJ Distributors">CJ Distributors</OPTION>

<OPTION value="Claritin">Claritin</OPTION>

<OPTION value="Clear Products">Clear Products</OPTION>

<OPTION value="Clif Bar">Clif Bar</OPTION>

<OPTION value="CMI Nutrition">CMI Nutrition</OPTION>

<OPTION value="Controlled Labs">Controlled Labs</OPTION>

<OPTION value="Country Life">Country Life</OPTION>

<OPTION value="CTD Labs">CTD Labs</OPTION>

<OPTION value="Cuur">Cuur</OPTION>

<OPTION value="Cytodyne Technologies">Cytodyne Technologies</OPTION>

<OPTION value="CytoSport">CytoSport</OPTION>

<OPTION value="D and E Pharmaceuticals">D and E Pharmaceuticals</OPTION>

<OPTION value="Dancing Paws">Dancing Paws</OPTION>

<OPTION value="Derma E">Derma E</OPTION>

<OPTION value="Dermavant Labs">Dermavant Labs</OPTION>

<OPTION value="Desert Essence">Desert Essence</OPTION>

<OPTION value="Designer Supplements">Designer Supplements</OPTION>

<OPTION value="Detoxify">Detoxify</OPTION>

<OPTION value="Devine Distribution">Devine Distribution</OPTION>

<OPTION value="Direct Marketing Concepts">Direct Marketing Concepts</OPTION>

<OPTION value="Discovery Herbs">Discovery Herbs</OPTION>

<OPTION value="Doctor's Best">Doctor's Best</OPTION>

<OPTION value="Dr. Christophers">Dr. Christophers</OPTION>

<OPTION value="Dr. Frank's">Dr. Frank's</OPTION>

<OPTION value="Dymatize Nutrition">Dymatize Nutrition</OPTION>

<OPTION value="Dynakor Pharmacal">Dynakor Pharmacal</OPTION>

<OPTION value="Dynamic Health Laboratories">Dynamic Health Laboratories</OPTION>

<OPTION value="Earth Science">Earth Science</OPTION>

<OPTION value="Earthrise">Earthrise</OPTION>

<OPTION value="EAS">EAS</OPTION>

<OPTION value="Eclectic Products">Eclectic Products</OPTION>

<OPTION value="Eclipse Sports Supplements">Eclipse Sports Supplements</OPTION>

<OPTION value="Ecoland">Ecoland</OPTION>

<OPTION value="Eden">Eden</OPTION>

<OPTION value="EGOceutical">EGOceutical</OPTION>

<OPTION value="Emerita">Emerita</OPTION>

<OPTION value="Enzymatic Therapy">Enzymatic Therapy</OPTION>

<OPTION value="Epic Nutrition">Epic Nutrition</OPTION>

<OPTION value="ErgoPharm">ErgoPharm</OPTION>

<OPTION value="ESSIAC Products">ESSIAC Products</OPTION>

<OPTION value="Esteem">Esteem</OPTION>

<OPTION value="Ethical Nutrients">Ethical Nutrients</OPTION>

<OPTION value="eVitamins">eVitamins</OPTION>

<OPTION value="Fearn">Fearn</OPTION>

<OPTION value="First Organics">First Organics</OPTION>

<OPTION value="Fizogen Precision Technologies">Fizogen Precision Technologies</OPTION>

<OPTION value="Flax Z Snax">Flax Z Snax</OPTION>

<OPTION value="Flora">Flora</OPTION>

<OPTION value="Food Force">Food Force</OPTION>

<OPTION value="Food Science of Vermont">Food Science of Vermont</OPTION>

<OPTION value="Forward Foods">Forward Foods</OPTION>

<OPTION value="Fountain of Youth">Fountain of Youth</OPTION>

<OPTION value="Fresh Wave">Fresh Wave</OPTION>

<OPTION value="FTH Nutraceuticals">FTH Nutraceuticals</OPTION>

<OPTION value="Futurebiotics">Futurebiotics</OPTION>

<OPTION value="Garden Greens">Garden Greens</OPTION>

<OPTION value="Garden of Life">Garden of Life</OPTION>

<OPTION value="Gaspari Nutrition">Gaspari Nutrition</OPTION>

<OPTION value="Generation Plus">Generation Plus</OPTION>

<OPTION value="Generix Laboratories">Generix Laboratories</OPTION>

<OPTION value="Genesis Today">Genesis Today</OPTION>

<OPTION value="Genisoy">Genisoy</OPTION>

<OPTION value="German Amer. Tech.">German Amer. Tech.</OPTION>

<OPTION value="GlaxoSmithKline">GlaxoSmithKline</OPTION>

<OPTION value="Global Labs">Global Labs</OPTION>

<OPTION value="Grandma Lucy's">Grandma Lucy's</OPTION>

<OPTION value="Grandpa's">Grandpa's</OPTION>

<OPTION value="Greek Island Labs">Greek Island Labs</OPTION>

<OPTION value="Green Foods">Green Foods</OPTION>

<OPTION value="Greens Today">Greens Today</OPTION>

<OPTION value="H57">H57</OPTION>

<OPTION value="Hain">Hain</OPTION>

<OPTION value="Harmonic Innerprizes">Harmonic Innerprizes</OPTION>

<OPTION value="Health From the Sun">Health From the Sun</OPTION>

<OPTION value="Health Plus Inc.">Health Plus Inc.</OPTION>

<OPTION value="Health Support">Health Support</OPTION>

<OPTION value="HealthSmart Foods">HealthSmart Foods</OPTION>

<OPTION value="Healthy Origins">Healthy Origins</OPTION>

<OPTION value="Healthy Relief">Healthy Relief</OPTION>

<OPTION value="Heaven And Earth">Heaven And Earth</OPTION>

<OPTION value="Heaven Sent Naturals">Heaven Sent Naturals</OPTION>

<OPTION value="Heel BHI for Homeopathy">Heel BHI for Homeopathy</OPTION>

<OPTION value="Herb Pharm">Herb Pharm</OPTION>

<OPTION value="Herbalife">Herbalife</OPTION>

<OPTION value="Herbasway Lab">Herbasway Lab</OPTION>

<OPTION value="Herbs for Kids">Herbs for Kids</OPTION>

<OPTION value="Hero">Hero</OPTION>

<OPTION value="Hi-Tech Pharmaceuticals">Hi-Tech Pharmaceuticals</OPTION>

<OPTION value="Himalaya Herbal Healthcare">Himalaya Herbal Healthcare</OPTION>

<OPTION value="Himalayan Institute">Himalayan Institute</OPTION>

<OPTION value="Hobe Laboratories">Hobe Laboratories</OPTION>

<OPTION value="Home Access">Home Access</OPTION>

<OPTION value="Home Health Products">Home Health Products</OPTION>

<OPTION value="Hot Stuff">Hot Stuff</OPTION>

<OPTION value="Howard Naturals">Howard Naturals</OPTION>

<OPTION value="Human Development">Human Development</OPTION>

<OPTION value="Hyland's">Hyland's</OPTION>

<OPTION value="I57 Ignite">I57 Ignite</OPTION>

<OPTION value="IDS Sports">IDS Sports</OPTION>

<OPTION value="Imperial Elixir">Imperial Elixir</OPTION>

<OPTION value="Improvita">Improvita</OPTION>

<OPTION value="Inholtra">Inholtra</OPTION>

<OPTION value="Inner Armour">Inner Armour</OPTION>

<OPTION value="Innovative Products">Innovative Products</OPTION>

<OPTION value="Instone">Instone</OPTION>

<OPTION value="ION Labs">ION Labs</OPTION>

<OPTION value="Iovate Health Sciences">Iovate Health Sciences</OPTION>

<OPTION value="Irwin Naturals">Irwin Naturals</OPTION>

<OPTION value="iSatori Global Technologies">iSatori Global Technologies</OPTION>

<OPTION value="ISS Research">ISS Research</OPTION>

<OPTION value="Jan Tana">Jan Tana</OPTION>

<OPTION value="Jarrow">Jarrow</OPTION>

<OPTION value="Jason Natural Cosmetics">Jason Natural Cosmetics</OPTION>

<OPTION value="Jason Winters">Jason Winters</OPTION>

<OPTION value="Kal">Kal</OPTION>

<OPTION value="Kay's Naturals">Kay's Naturals</OPTION>

<OPTION value="Kcep Laboratories">Kcep Laboratories</OPTION>

<OPTION value="Kemistry">Kemistry</OPTION>

<OPTION value="Kendy USA">Kendy USA</OPTION>

<OPTION value="KingBio Natural Medicine">KingBio Natural Medicine</OPTION>

<OPTION value="Kiss My Face">Kiss My Face</OPTION>

<OPTION value="Klein-Becker">Klein-Becker</OPTION>

<OPTION value="KMS">KMS</OPTION>

<OPTION value="Knight-McDowell Labs">Knight-McDowell Labs</OPTION>

<OPTION value="Kolorex">Kolorex</OPTION>

<OPTION value="Kroeger Herb">Kroeger Herb</OPTION>

<OPTION value="Kyolic">Kyolic</OPTION>

<OPTION value="L.A. Naturals">L.A. Naturals</OPTION>

<OPTION value="Labrada Nutrition">Labrada Nutrition</OPTION>

<OPTION value="Lamas Beauty">Lamas Beauty</OPTION>

<OPTION value="Lane Labs">Lane Labs</OPTION>

<OPTION value="Larenim Mineral Makeup">Larenim Mineral Makeup</OPTION>

<OPTION value="Larrea Biosciences">Larrea Biosciences</OPTION>

<OPTION value="Learner's Edge">Learner's Edge</OPTION>

<OPTION value="Lexxus International">Lexxus International</OPTION>

<OPTION value="LG Sciences">LG Sciences</OPTION>

<OPTION value="Libido Edge">Libido Edge</OPTION>

<OPTION value="Liddell Laboratories">Liddell Laboratories</OPTION>

<OPTION value="Life Extension">Life Extension</OPTION>

<OPTION value="Life-Flo">Life-Flo</OPTION>

<OPTION value="Lily of the Desert">Lily of the Desert</OPTION>

<OPTION value="Liquid Health">Liquid Health</OPTION>

<OPTION value="Loanda Herbal Soaps">Loanda Herbal Soaps</OPTION>

<OPTION value="Lucky Tiger">Lucky Tiger</OPTION>

<OPTION value="Luna Bars">Luna Bars</OPTION>

<OPTION value="M.D. Science Lab">M.D. Science Lab</OPTION>

<OPTION value="Macro Life Naturals">Macro Life Naturals</OPTION>

<OPTION value="Maitake Products Inc">Maitake Products Inc</OPTION>

<OPTION value="Maritz Mayer">Maritz Mayer</OPTION>

<OPTION value="Max Factor">Max Factor</OPTION>

<OPTION value="Maximum Human Performance">Maximum Human Performance</OPTION>

<OPTION value="Maximum International">Maximum International</OPTION>

<OPTION value="Maximum Living">Maximum Living</OPTION>

<OPTION value="Maximum Nutrients">Maximum Nutrients</OPTION>

<OPTION value="Medi+Straw">Medi+Straw</OPTION>

<OPTION value="Medical Futures Inc">Medical Futures Inc</OPTION>

<OPTION value="MedSpan Laboratories">MedSpan Laboratories</OPTION>

<OPTION value="MET-Rx">MET-Rx</OPTION>

<OPTION value="Metabolic Response Modifiers">Metabolic Response Modifiers</OPTION>

<OPTION value="Michael's">Michael's</OPTION>

<OPTION value="Michelle's Miracle">Michelle's Miracle</OPTION>

<OPTION value="Mill Creek">Mill Creek</OPTION>

<OPTION value="MLO">MLO</OPTION>

<OPTION value="MMUSA Muscle Marketing USA">MMUSA Muscle Marketing USA</OPTION>

<OPTION value="ModuCare (EPI)">ModuCare (EPI)</OPTION>

<OPTION value="Molecular Nutrition">Molecular Nutrition</OPTION>

<OPTION value="Montana">Montana</OPTION>

<OPTION value="Morter HealthSystem">Morter HealthSystem</OPTION>

<OPTION value="Muscle Fortress">Muscle Fortress</OPTION>

<OPTION value="MuscleTech">MuscleTech</OPTION>

<OPTION value="MyoMed">MyoMed</OPTION>

<OPTION value="Nasaline">Nasaline</OPTION>

<OPTION value="National Health Products">National Health Products</OPTION>

<OPTION value="Natra-Bio">Natra-Bio</OPTION>

<OPTION value="Natracare">Natracare</OPTION>

<OPTION value="Natren">Natren</OPTION>

<OPTION value="Natrol">Natrol</OPTION>

<OPTION value="Naturade">Naturade</OPTION>

<OPTION value="Natural Balance">Natural Balance</OPTION>

<OPTION value="Natural Care">Natural Care</OPTION>

<OPTION value="Natural Miracles">Natural Miracles</OPTION>

<OPTION value="Natural Pet Pharmaceuticals">Natural Pet Pharmaceuticals</OPTION>

<OPTION value="Natural Product Solutions">Natural Product Solutions</OPTION>

<OPTION value="Natural Sources">Natural Sources</OPTION>

<OPTION value="Natural Sport">Natural Sport</OPTION>

<OPTION value="Natural Vitality">Natural Vitality</OPTION>

<OPTION value="Naturally">Naturally</OPTION>

<OPTION value="NaturalMax">NaturalMax</OPTION>

<OPTION value="Nature Works">Nature Works</OPTION>

<OPTION value="Nature's Answer">Nature's Answer</OPTION>

<OPTION value="Nature's Benefit">Nature's Benefit</OPTION>

<OPTION value="Nature's Best">Nature's Best</OPTION>

<OPTION value="Nature's Gate">Nature's Gate</OPTION>

<OPTION value="Nature's Gift">Nature's Gift</OPTION>

<OPTION value="Nature's Herbs">Nature's Herbs</OPTION>

<OPTION value="Nature's Life">Nature's Life</OPTION>

<OPTION value="Nature's Perfect">Nature's Perfect</OPTION>

<OPTION value="Nature's Plus">Nature's Plus</OPTION>

<OPTION value="Nature's Renewal">Nature's Renewal</OPTION>

<OPTION value="Nature's Secret">Nature's Secret</OPTION>

<OPTION value="Nature's Way">Nature's Way</OPTION>

<OPTION value="NatureMost">NatureMost</OPTION>

<OPTION value="Natures Harmony">Natures Harmony</OPTION>

<OPTION value="New Wave Enviro">New Wave Enviro</OPTION>

<OPTION value="NewChapter">NewChapter</OPTION>

<OPTION value="Next Proteins">Next Proteins</OPTION>

<OPTION value="Nirvana Natural">Nirvana Natural</OPTION>

<OPTION value="Nordic Naturals">Nordic Naturals</OPTION>

<OPTION value="North American Herb And Spice">North American Herb And Spice</OPTION>

<OPTION value="Novogen">Novogen</OPTION>

<OPTION value="Now">Now</OPTION>

<OPTION value="NuAge Homeopathic Remedies">NuAge Homeopathic Remedies</OPTION>

<OPTION value="Nutiva">Nutiva</OPTION>

<OPTION value="Nutrabolics">Nutrabolics</OPTION>

<OPTION value="NutraLab">NutraLab</OPTION>

<OPTION value="NutraMax Laboratories">NutraMax Laboratories</OPTION>

<OPTION value="Nutramerica">Nutramerica</OPTION>

<OPTION value="Nutrapathic">Nutrapathic</OPTION>

<OPTION value="NutraQuest. Inc.">NutraQuest. Inc.</OPTION>

<OPTION value="Nutrex">Nutrex</OPTION>

<OPTION value="Nutricology">Nutricology</OPTION>

<OPTION value="Nutricor Labs">Nutricor Labs</OPTION>

<OPTION value="Nutritech">Nutritech</OPTION>

<OPTION value="Nutrition Now">Nutrition Now</OPTION>

<OPTION value="Nutriworks">Nutriworks</OPTION>

<OPTION value="NV Inc.">NV Inc.</OPTION>

<OPTION value="NVE Pharmaceuticals">NVE Pharmaceuticals</OPTION>

<OPTION value="Nx Labs">Nx Labs</OPTION>

<OPTION value="Ola Loa">Ola Loa</OPTION>

<OPTION value="Olympian Labs">Olympian Labs</OPTION>

<OPTION value="Only Natural">Only Natural</OPTION>

<OPTION value="Optimum Nutrition">Optimum Nutrition</OPTION>

<OPTION value="Organic India">Organic India</OPTION>

<OPTION value="OxyLife">OxyLife</OPTION>

<OPTION value="Pacific Health">Pacific Health</OPTION>

<OPTION value="Palo Alto Labs">Palo Alto Labs</OPTION>

<OPTION value="Pbl">Pbl</OPTION>

<OPTION value="Peaceful Mountain">Peaceful Mountain</OPTION>

<OPTION value="PerCoBa">PerCoBa</OPTION>

<OPTION value="Pet Aromatics">Pet Aromatics</OPTION>

<OPTION value="Pet Naturals of Vermont">Pet Naturals of Vermont</OPTION>

<OPTION value="PetMax Naturals">PetMax Naturals</OPTION>

<OPTION value="PhytoPharmica®">PhytoPharmica®</OPTION>

<OPTION value="Pines International">Pines International</OPTION>

<OPTION value="Pinnacle">Pinnacle</OPTION>

<OPTION value="Pioneer">Pioneer</OPTION>

<OPTION value="Planetary Formulas">Planetary Formulas</OPTION>

<OPTION value="Powerbar">Powerbar</OPTION>

<OPTION value="Powerbutter">Powerbutter</OPTION>

<OPTION value="Premier Marketing">Premier Marketing</OPTION>

<OPTION value="Premier One">Premier One</OPTION>

<OPTION value="Prevention">Prevention</OPTION>

<OPTION value="Prilosec">Prilosec</OPTION>

<OPTION value="PrimaForce">PrimaForce</OPTION>

<OPTION value="Pro Tan">Pro Tan</OPTION>

<OPTION value="Prolab Nutrition">Prolab Nutrition</OPTION>

<OPTION value="Promax Nutrition">Promax Nutrition</OPTION>

<OPTION value="Pronatura">Pronatura</OPTION>

<OPTION value="Proper Nutrition">Proper Nutrition</OPTION>

<OPTION value="Proto Foods">Proto Foods</OPTION>

<OPTION value="Pure and Basic">Pure and Basic</OPTION>

<OPTION value="Pure Essence Labs">Pure Essence Labs</OPTION>

<OPTION value="Pure Fruit Technologies">Pure Fruit Technologies</OPTION>

<OPTION value="Pure Planet">Pure Planet</OPTION>

<OPTION value="Pure Source">Pure Source</OPTION>

<OPTION value="Purest Colloids">Purest Colloids</OPTION>

<OPTION value="Puriclean">Puriclean</OPTION>

<OPTION value="Quality of Life">Quality of Life</OPTION>

<OPTION value="Quantum">Quantum</OPTION>

<OPTION value="Queen Helene">Queen Helene</OPTION>

<OPTION value="R Garden">R Garden</OPTION>

<OPTION value="Rachel Perry">Rachel Perry</OPTION>

<OPTION value="Rainbow Light">Rainbow Light</OPTION>

<OPTION value="Rand Research Labs">Rand Research Labs</OPTION>

<OPTION value="Renew Life">Renew Life</OPTION>

<OPTION value="Reviva Labs">Reviva Labs</OPTION>

<OPTION value="Ridgecrest">Ridgecrest</OPTION>

<OPTION value="RNY Group">RNY Group</OPTION>

<OPTION value="Rodial">Rodial</OPTION>

<OPTION value="Rogaine">Rogaine</OPTION>

<OPTION value="San Nutrition">San Nutrition</OPTION>

<OPTION value="Sanhelios">Sanhelios</OPTION>

<OPTION value="Sante Active">Sante Active</OPTION>

<OPTION value="Scandinavian Formulas">Scandinavian Formulas</OPTION>

<OPTION value="Schiff">Schiff</OPTION>

<OPTION value="SciFit">SciFit</OPTION>

<OPTION value="SciTec Nutrition">SciTec Nutrition</OPTION>

<OPTION value="Sedona Labs">Sedona Labs</OPTION>

<OPTION value="ShiKai">ShiKai</OPTION>

<OPTION value="Silver Lake Research">Silver Lake Research</OPTION>

<OPTION value="Similasan">Similasan</OPTION>

<OPTION value="Size 0 Labs">Size 0 Labs</OPTION>

<OPTION value="Slimage">Slimage</OPTION>

<OPTION value="SlimQuick Laboratories">SlimQuick Laboratories</OPTION>

<OPTION value="SmartBurn">SmartBurn</OPTION>

<OPTION value="Smith Sorensen">Smith Sorensen</OPTION>

<OPTION value="SNAC">SNAC</OPTION>

<OPTION value="Solaray">Solaray</OPTION>

<OPTION value="SolarChem Labs">SolarChem Labs</OPTION>

<OPTION value="Solgar">Solgar</OPTION>

<OPTION value="Source Naturals">Source Naturals</OPTION>

<OPTION value="South Pacific Trading">South Pacific Trading</OPTION>

<OPTION value="Spectrum">Spectrum</OPTION>

<OPTION value="Spirit Sciences USA">Spirit Sciences USA</OPTION>

<OPTION value="St. Paul Brands">St. Paul Brands</OPTION>

<OPTION value="Stakich, Inc">Stakich, Inc</OPTION>

<OPTION value="StarChem Labs">StarChem Labs</OPTION>

<OPTION value="Sterling-Grant Laboratories">Sterling-Grant Laboratories</OPTION>

<OPTION value="Sunny Green">Sunny Green</OPTION>

<OPTION value="Superior Source">Superior Source</OPTION>

<OPTION value="Supplement Training Systems">Supplement Training Systems</OPTION>

<OPTION value="Symbiotics">Symbiotics</OPTION>

<OPTION value="Syntrax">Syntrax</OPTION>

<OPTION value="Teeccino">Teeccino</OPTION>

<OPTION value="TestMedica">TestMedica</OPTION>

<OPTION value="The Magic Pill Inc">The Magic Pill Inc</OPTION>

<OPTION value="The Nutrition Farm">The Nutrition Farm</OPTION>

<OPTION value="The Real Food Trading Company">The Real Food Trading Company</OPTION>

<OPTION value="The Synergy Company">The Synergy Company</OPTION>

<OPTION value="Thermolife">Thermolife</OPTION>

<OPTION value="Thompson">Thompson</OPTION>

<OPTION value="Thunder Ridge">Thunder Ridge</OPTION>

<OPTION value="Thursday Plantation">Thursday Plantation</OPTION>

<OPTION value="Tiger's Milk">Tiger's Milk</OPTION>

<OPTION value="Tom's of Maine">Tom's of Maine</OPTION>

<OPTION value="Traditional Medicinals">Traditional Medicinals</OPTION>

<OPTION value="Tri-O-Plex">Tri-O-Plex</OPTION>

<OPTION value="TriMedica">TriMedica</OPTION>

<OPTION value="TriPharma">TriPharma</OPTION>

<OPTION value="Trojan">Trojan</OPTION>

<OPTION value="Tropical Oasis">Tropical Oasis</OPTION>

<OPTION value="Twinlab">Twinlab</OPTION>

<OPTION value="Tyler Encapsulations">Tyler Encapsulations</OPTION>

<OPTION value="UAS Labs">UAS Labs</OPTION>

<OPTION value="Ultimate Nutrition">Ultimate Nutrition</OPTION>

<OPTION value="Ultralab Nutrition">Ultralab Nutrition</OPTION>

<OPTION value="Universal Nutrition">Universal Nutrition</OPTION>

<OPTION value="Urban Biologics">Urban Biologics</OPTION>

<OPTION value="Valeo Fitness Gear">Valeo Fitness Gear</OPTION>

<OPTION value="VegLife">VegLife</OPTION>

<OPTION value="Viridis Laboratories">Viridis Laboratories</OPTION>

<OPTION value="Vital Basics">Vital Basics</OPTION>

<OPTION value="VitaLabs">VitaLabs</OPTION>

<OPTION value="Vitaline Formulas">Vitaline Formulas</OPTION>

<OPTION value="Vitanica">Vitanica</OPTION>

<OPTION value="Vitol">Vitol</OPTION>

<OPTION value="VPX">VPX</OPTION>

<OPTION value="Vyotech">Vyotech</OPTION>

<OPTION value="Wally's">Wally's</OPTION>

<OPTION value="Weider">Weider</OPTION>

<OPTION value="Weil">Weil</OPTION>

<OPTION value="Weleda">Weleda</OPTION>

<OPTION value="Wellements">Wellements</OPTION>

<OPTION value="Window Rock">Window Rock</OPTION>

<OPTION value="Wisdom of the Ancients">Wisdom of the Ancients</OPTION>

<OPTION value="World Nutrition">World Nutrition</OPTION>

<OPTION value="World Organic">World Organic</OPTION>

<OPTION value="Wuyi Rock Tea">Wuyi Rock Tea</OPTION>

<OPTION value="Xyience">Xyience</OPTION>

<OPTION value="Yerba Prima">Yerba Prima</OPTION>

<OPTION value="Yogi Tea Organic Teas">Yogi Tea Organic Teas</OPTION>

<OPTION value="Youthful Essentials">Youthful Essentials</OPTION>

<OPTION value="Zand">Zand</OPTION>

<OPTION value="ZenCore">ZenCore</OPTION>

<OPTION value="Zenergize">Zenergize</OPTION>

<OPTION value="Zicam">Zicam</OPTION>

<OPTION value="Zoller Labratories">Zoller Labratories</OPTION>

<OPTION value="Zone Perfect">Zone Perfect</OPTION>
</select>
<input type="submit" value=" GO ">
</form></TD>
<TD align=center width=33% bgcolor=#ffffff valign=top>
<form method=post action=search.php>
<input type=text name=search size=12>
<input type=submit value=" Search ">
</form></TD>
</TR></Table>
<!---Top Stuff--->

<!---Content Stuff--->
<table border=0 width=98% cellpadding=5 cellspacing=0 align=center bgcolor=#ffffff>
<TR>

<TD align=left width=15% bgcolor=#ffffff valign=top>
<b>By Category</b><br><br>
<a href="index.php">Main Entrance</A><br>
<a href="brandshop.php">List All Brands</A><br><br>

<a href="category.php?cid=91">Acidophilus</A><br>

<a href="category.php?cid=77">Allergy</A><br>

<a href="category.php?cid=49">Amino Acids</A><br>

<a href="category.php?cid=3">Antioxidants</A><br>

<a href="category.php?cid=92">Anxiety</A><br>

<a href="category.php?cid=4">Arthritis - Joints</A><br>

<a href="category.php?cid=103">Bars</A><br>

<a href="category.php?cid=5">Blood Pressure</A><br>

<a href="category.php?cid=6">Bones</A><br>

<a href="category.php?cid=104">Books</A><br>

<a href="category.php?cid=7">Brain - Memory</A><br>

<a href="category.php?cid=8">Cancer</A><br>

<a href="category.php?cid=9">Childrens</A><br>

<a href="category.php?cid=10">Cholesterol</A><br>

<a href="category.php?cid=11">Circulation</A><br>

<a href="category.php?cid=12">Cold - Flu</A><br>

<a href="category.php?cid=90">Colon</A><br>

<a href="category.php?cid=30">Depression</A><br>

<a href="category.php?cid=13">Detox</A><br>

<a href="category.php?cid=14">Diabetes</A><br>

<a href="category.php?cid=71">Diets</A><br>

<a href="category.php?cid=47">Digestion</A><br>

<a href="category.php?cid=15">Energy</A><br>

<a href="category.php?cid=75">Facial Care</A><br>

<a href="category.php?cid=88">Glandulars</A><br>

<a href="category.php?cid=94">Green Foods</A><br>

<a href="category.php?cid=96">Growth Hormones</A><br>

<a href="category.php?cid=74">Hair Care</A><br>

<a href="category.php?cid=95">Hangover</A><br>

<a href="category.php?cid=50">Headaches</A><br>

<a href="category.php?cid=87">Hearing - Ears</A><br>

<a href="category.php?cid=17">Heart Support</A><br>

<a href="category.php?cid=62">Herbs</A><br>

<a href="category.php?cid=60">Immune System</A><br>

<a href="category.php?cid=25">Kidney - Bladder</A><br>

<a href="category.php?cid=19">Liver</A><br>

<a href="category.php?cid=73">Lotions - Creams</A><br>

<a href="category.php?cid=105">Low Carb</A><br>

<a href="category.php?cid=31">Lungs</A><br>

<a href="category.php?cid=23">Menopause</A><br>

<a href="category.php?cid=20">Mens Health</A><br>

<a href="category.php?cid=29">Minerals</A><br>

<a href="category.php?cid=63">Miscellaneous</A><br>

<a href="category.php?cid=101">Mouth Care</A><br>

<a href="category.php?cid=76">Nail Care</A><br>

<a href="category.php?cid=97">Noni</A><br>

<a href="category.php?cid=65">Oils</A><br>

<a href="category.php?cid=85">Pain Relievers</A><br>

<a href="category.php?cid=78">Personal Care</A><br>

<a href="category.php?cid=100">Pet Care</A><br>

<a href="category.php?cid=22">PMS</A><br>

<a href="category.php?cid=102">Proteins</A><br>

<a href="category.php?cid=21">Rest & Relax</A><br>

<a href="category.php?cid=51">Sexual Help</A><br>

<a href="category.php?cid=16">Skin Care</A><br>

<a href="category.php?cid=99">Smoking</A><br>

<a href="category.php?cid=32">Sports Nutrition</A><br>

<a href="category.php?cid=24">Stress</A><br>

<a href="category.php?cid=93">Teenagers Health</A><br>

<a href="category.php?cid=33">Vision</A><br>

<a href="category.php?cid=52">Vitamin A</A><br>

<a href="category.php?cid=53">Vitamin B</A><br>

<a href="category.php?cid=54">Vitamin C</A><br>

<a href="category.php?cid=55">Vitamin D</A><br>

<a href="category.php?cid=56">Vitamin E</A><br>

<a href="category.php?cid=89">Vitamin K</A><br>

<a href="category.php?cid=57">Vitamin Multiple</A><br>

<a href="category.php?cid=27">Weight Loss</A><br>

<a href="category.php?cid=26">Womens Health</A><br>
</TD>
<TD align=left width=70% bgcolor=#ffffff valign=top>

<b>AchievOne Products, Supplements, & Vitamins</b><br><br>


<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>
<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13351">
<img src="http://www.evitamins.com/images/products/http://www.evitamins.com/images/products/AOcapp.jpg&sharpenvalue=&Rotate=0" border="0" alt="AchievOne Cappuccino" align="left"></A>
</TD>

<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13351">AchievOne Cappuccino</A><br>
Made By: <a href="brand.php?brandname=AchievOne">AchievOne</A><br>
$44.95 for 1 Case (12 Bottles)<br>
achievONE  is the revolutionary nutritional coffee beverage that&#8217;s arrived at the most opportune of times. Consumers in search of alternative beverages that are both healthy and taste great need look ... <a href="product.php?skew=13351">More Info >>></A>
</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>
<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>
<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13352">

<img src="http://www.evitamins.com/images/products/http://www.evitamins.com/images/products/AOhazelnut.jpg&sharpenvalue=&Rotate=0" border="0" alt="AchievOne Hazelnut Creme" align="left"></A>
</TD>
<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13352">AchievOne Hazelnut Creme</A><br>
Made By: <a href="brand.php?brandname=AchievOne">AchievOne</A><br>
$44.95 for 1 Case (12 Bottles)<br>
achievONE  is the revolutionary nutritional coffee beverage that&#8217;s arrived at the most opportune of times. Consumers in search of alternative beverages that are both healthy and taste great need look ... <a href="product.php?skew=13352">More Info >>></A>
</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>
<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>

<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13353">
<img src="http://www.evitamins.com/images/products/http://www.evitamins.com/images/products/AOmochajava.jpg&sharpenvalue=&Rotate=0" border="0" alt="AchievOne Mocha Java" align="left"></A>
</TD>
<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13353">AchievOne Mocha Java</A><br>
Made By: <a href="brand.php?brandname=AchievOne">AchievOne</A><br>
$44.95 for 1 Case (12 Bottles)<br>
achievONE  is the revolutionary nutritional coffee beverage that&#8217;s arrived at the most opportune of times. Consumers in search of alternative beverages that are both healthy and taste great need look ... <a href="product.php?skew=13353">More Info >>></A>
</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>

<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>
<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13354">
<img src="http://www.evitamins.com/images/products/http://www.evitamins.com/images/products/AOvanilla.jpg&sharpenvalue=&Rotate=0" border="0" alt="AchievOne Vanilla Nut" align="left"></A>
</TD>
<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href="product.php?skew=13354">AchievOne Vanilla Nut</A><br>
Made By: <a href="brand.php?brandname=AchievOne">AchievOne</A><br>
$44.95 for 1 Case (12 Bottles)<br>
achievONE  is the revolutionary nutritional coffee beverage that&#8217;s arrived at the most opportune of times. Consumers in search of alternative beverages that are both healthy and taste great need look ... <a href="product.php?skew=13354">More Info >>></A>

</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>
</TD>
<TD align=left width=15% bgcolor=#ffffff valign=top>
<b><font color=#CC0000><u>Current Specials</u></font></b><br><br>

<b>49% OFF NO-Xplode</b><br>
NO-Xplode for 49% off retail!<br>
<b>Code:</b> Not Needed<br>
<b>Expires:</b> 09/09/2008<br>

<a href="product.php?skew=5722">Product Details</A><br><br>

<b>20% OFF Dianabol</b><br>
Dianabol extreme maximum anabolic agent<br>
<b>Code:</b> Not Needed<br>
<b>Expires:</b> 09/09/2008<br>
<a href="product.php?skew=5964">Product Details</A><br><br>

<b>63% OFF Daily One Caps By Twinlab</b><br>
<center><img src=http://www.evitamins.com/images/products/thumbnails/dailyoneTWLAB.gif></center><br>Clearance Special (while supplies last)<br>
<b>Code:</b> Not Needed<br>
<b>Expires:</b> <br>
<a href="product.php?skew=3779">Product Details</A><br><br>

<b>FREE Shipping on Zantrex-3</b><br>

Receive free standard shipping on your entire order when you buy Zantrex-3.<br>
<b>Code:</b> Not Needed<br>
<b>Expires:</b> 09/09/2008<br>
<a href="product.php?skew=1879">Product Details</A><br><br>

<b>20% OFF Face Lift</b><br>
Experience the 7 minute face lift!<br>

<b>Code:</b> Not Needed<br>
<b>Expires:</b> 09/09/2008<br>
<a href="product.php?skew=6127">Product Details</A><br><br>
<br><b>Liquidation Special</b> - 20% to 70% OFF <a href=http://www.evitamins.com/affiliates/aw.asp?B=1&A=1&Task=Click>vitamins</a>.<br><br><br><b>Discount <a href=http://www.evitamins.com/affiliates/aw.asp?B=1&A=1&Task=Click&targetURL=http://www.evitamins.com/sportsnutrition_main.asp>bodybuilding supplements</a>.<br><br></TD>

</TR></Table>
<!---Content Stuff--->

<!---- CHANGE COPYRIGHT INFO TO YOUR OWN SITE ---->
<center>
<font size=1>
Last Updated: June 23, 2008<br>
Copyright &copy 2004 - <a href="http://www.evitamins1.com">eVitamins1.com</A>
</font>
</center>
</body>
</html>

---

### Post by alphane on 2008-06-24
Have you tried manually adding in an image and working backwards to debug?

Explicitly code out an image to see if that appears.  I'm no PHP pro, and when I last installed my development server at home, I had some wierd permission problems from stopping any of my images being readable, so that's worth a check too?

---

### Post by Gunman1982 on 2008-06-24
Cough:
<img src="http://www.evitamins.com/images/products/http://www.evitamins.com/images/products/AOvanilla.jpg&sharpenvalue=&Rotate=0" border="0" alt="AchievOne Vanilla Nut" align="left"></A>

maaaaybe you should change the code in your file to 
```

<img src="<? echo $row[image]; ?>" border="0" alt="<? echo $row[name]; ?>" align="left"></A>

```

---

### Post by CrusaderAD on 2008-06-24
I just got that too... (shakes head) one dang quote. I'm both happy and upset. Thanks for all the great posts!

---

