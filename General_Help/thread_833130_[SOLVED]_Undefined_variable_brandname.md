---
title: "[SOLVED] Undefined variable: brandname"
date: 2008-06-18
forum: General Help
---

### Post by CrusaderAD on 2008-06-18
Hello. I'm having a problem defining a variable. I get this error:

<errorentry>
	<datetime>2008-06-18 10:50:19 (EDT)</datetime>
	<errornum>8</errornum>
	<errortype>Notice</errortype>
	<errormsg>Undefined variable: brandname</errormsg>
	<scriptname>/home/evitamins/websites/evitamins1/teststore/brand.php</scriptname>
	<scriptlinenum>4</scriptlinenum>
</errorentry>



Here is the script:



<?
include("config.php");
include("error.php");
$brand2=stripslashes($brandname);

$brandname = (isset($_GET['brandname'])) ? $_GET['brandname']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;

?>
<html>
<head>
<title>Vitamins & Supplements Made By <? echo $brand2; ?></title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<META NAME="description" CONTENT="<? echo $brand2; ?> health vitamins and supplements.">
<META NAME="keywords" CONTENT="<? echo $brand2; ?>">
<meta name="Language" content="en">
<meta name="Distribution" content="global">
<meta name="author" content="<? echo $brand2; ?>">
<META NAME="robots" CONTENT="index,follow">

<? include("style.php"); ?>

</head>

<body topmargin="15" bgcolor=#ffffff>

<H1 align=center>Vitamins & Supplements Made By <? echo $brand2; ?></H1>
<H2 align=center><? echo $brand2; ?> Supplements & Vitamins</H2>

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

<b><? echo $brand2; ?> Products, Supplements, & Vitamins</b><br><br>

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
        WHERE brand='$brandname'
	   ";
if(mysql_num_rows(mysql_query($sql)) < 1){
echo "Error!";
}

// Get Products Within The Category Below
$result = mysql_query("select * from evitamins_products WHERE brand='$brandname' ORDER by brand ASC LIMIT $start, $limit") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
include("show-thumbnail.php");
}

$prv = ($start-$limit);
$nxt = ($start+$limit);
if($prv < 0){
$previous = "";
}else {
$previous = "<a href=\"brand.php?brandname=$bran2&start=$prv&limit=$limit\"><<< Previous $limit Products From $brand2</a>";
}
if(mysql_num_rows(mysql_query($sql)) < $nxt){
$next = "";
}else {
$next = "<a href=\"brand.php?brandname=$brand2&start=$nxt&limit=$limit\">Next $limit Products From $brand2 >>></a>";
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

### Post by CrusaderAD on 2008-06-18
I changed the variables to:

$brandname = (isset($_GET['brandname'])) ? $_GET['brandname']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;
$brand2 = (isset($_GET['brand2'])) ? $_GET['brand2'] : null;
$brand2 = stripslashes($brandname);

But now it doesn't give me an error in the log. It just doesn't load the page...

---

### Post by MacAnthony on 2008-06-18
You are setting the variable twice with 2 different values here:

```

$brand2 = (isset($_GET['brand2'])) ? $_GET['brand2'] : null;
$brand2 = stripslashes($brandname);

```

The firs line becomes irrelevant after it's overwritten by the second line.

I don't see anything syntactically wrong with the provided code though. No reason it shouldn't display some output. I would comment out the first lines to see which one is causing the issue. Possibly one of the included files on the top of the file.

---

### Post by CrusaderAD on 2008-06-18
I commented out a few things in a few ways and I still get the "Error!" page. Here's the code that pertains to this:

$sql = "SELECT *
	    FROM evitamins_products
        WHERE brand='$brandname'
	   ";
if(mysql_num_rows(mysql_query($sql)) < 1){
echo "Error!";

Like it's not pulling the data, but it's there will all of the connections made... strange.

---

### Post by CrusaderAD on 2008-06-18
I forgot to mention that this code uses a drop down form. Here is the code:


<form method="post" action="brand.php">
<select name="brandname">
<OPTION value="0">Shop By Brand</OPTION>
<?
$result = mysql_query("select * from brands ORDER by brandname ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row[brandname]\">$row[brandname]</OPTION>
";
}
mysql_free_result($result);
?>
</select>
<input type="submit" value=" GO ">
</form>


Maybe this is where I'm getting the error?

---

### Post by MacAnthony on 2008-06-18
```

$sql = "SELECT *
FROM evitamins_products
WHERE brand='$brandname'
";
if(**mysql_num_rows(mysql_query($sql)) < 1**){
echo "Error!";

```

Just cause a query doesn't return results, it doesn't mean there is an error. What if the query executes fine but there aren't any matching results?

---

### Post by MacAnthony on 2008-06-18
This again, shouldn't prevent it from running, but this:

```

while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row[brandname]\">$row[brandname]</OPTION>
";
}

```

Should be changed to this:

```

while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row['brandname']\">$row['brandname']</OPTION>
";
}

```

Index values are strings so they should be enclosed in quotes.

---

### Post by CrusaderAD on 2008-06-18
Ok... this script runs on a linux server through a hosting company. Everything works fine when it's on their server, but when the script is ran on another outside server, it results in error. So it pulls data when the database is on the same machine, but when we try to tap in remotely, it gives us no results. I made sure the categories that I am attempting to pull have data. It works on the local server, but not on any remote servers. When I defined the variables (changed the code) I was able to pull up data when just viewing the page. When I try to use a form (drop down menu), it doesn't work. When I put the quotes in like you suggested I got this error:

Parse error: syntax error, unexpected T_ENCAPSED_AND_WHITESPACE, expecting T_STRING or T_VARIABLE or T_NUM_STRING in /home/evitamins/websites/evitamins1/teststore/brands-drop-down.php on line 9


Here's the code:


<form method="post" action="brand.php">
<select name="brandname">
<OPTION value="0">Shop By Brand</OPTION>
<?
$result = mysql_query("select * from brands ORDER by brandname ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row['brandname']\">$row['brandname']</OPTION>
";
}
mysql_free_result($result);
?>
</select>
<input type="submit" value=" GO ">
</form>


Thanks for all your help!

---

### Post by MacAnthony on 2008-06-18
Ah yes it would.

Sorry about that. Since you are referring to an array, you need to let it know that you are references a variable and mark it with {} curly brackets. Like:
```

while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"{$row['brandname']}\">{$row['brandname']}</OPTION>
";
}

```

---

### Post by CrusaderAD on 2008-06-18
It's basically come down to this... the entire site works except for the forms (drop down menus). The form pulls up the "brands" or "categories" correctly, but when I click on one, it gives me the error page. Here are the forms:

----------------Categories---------------------

<form method="post" action="category.php">
<select name=cid>
<OPTION value="0">Shop By Category</OPTION>
<?
$result = mysql_query("select * from categories ORDER by catname ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row[cid]\">$row[catname]</OPTION>
";
}
mysql_free_result($result);
?>
</select>
<input type="submit" value=" GO ">
</form>

----------------Brands--------------------

<form method="post" action="brand.php">
<select name="brandname">
<OPTION value="0">Shop By Brand</OPTION>
<?
$result = mysql_query("select * from brands ORDER by brandname ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
echo "
<OPTION value=\"$row[brandname]\">$row[brandname]</OPTION>
";
}
mysql_free_result($result);
?>
</select>
<input type="submit" value=" GO ">
</form>

---

### Post by MacAnthony on 2008-06-18
When you have something referenced like $row[cid], it thinks it's looking for an array with the index of cid, but since cid isn't in quotes (like it should be) it thinks it's a constant variable. So unless there is a constant defined of cid, it isn't going to work. What you want is to go the the 'cid' index of the array, so you need to refer to it as $row['cid'], etc.

For that to work inside of a string, you either need to escape from the string or tell php that this portion of the string is a variable and not a string.

To escape from the string, you need to end the string and concatenate it like so:
echo "<option value=\"" . $row['cid'] . "\">" . $row['catname'] . "</option>";

Or to mark it with {} like so:
echo "<option value=\"{$row['cid']}\">{$row['catname']}</option>";

Either way is acceptable, but if you do option 2, you have to make sure you have no spaces between the brackets {}.


I'm not sure what error page you are getting, but if I could see the browser source output of at least this portion of the form, I could tell you if it's this variable issue or if the query itself isn't working.

---

### Post by CrusaderAD on 2008-06-18
I put the curly brackets in the code, same error result.

---

### Post by CrusaderAD on 2008-06-18
Here's the output source:

  
<html>
<head>
<title>Vitamins & Supplements Made By </title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<META NAME="description" CONTENT=" health vitamins and supplements.">
<META NAME="keywords" CONTENT="">
<meta name="Language" content="en">
<meta name="Distribution" content="global">
<meta name="author" content="">
<META NAME="robots" CONTENT="index,follow">

<style type="text/css">
	body,td			{ font-family: Arial, Helvetica, sans-serif; color: #000000; font-size: 11px; }
	A:link			{ text-decoration: underline; color: #000099; }
	A:visited		{ text-decoration: underline; color: #000099; }
	A:hover			{ text-decoration: underline; color: #000000; }
</style>
</head>

<body topmargin="15" bgcolor=#ffffff>

<H1 align=center>Vitamins & Supplements Made By </H1>
<H2 align=center> Supplements & Vitamins</H2>

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

<OPTION value="4 Your Health">4 Your Health</OPTION

<OPTION value="4everPets">4everPets</OPTION

<OPTION value="Abkit">Abkit</OPTION

<OPTION value="Abra Therapeutic">Abra Therapeutic</OPTION

<OPTION value="Absolute Nutrition">Absolute Nutrition</OPTION

<OPTION value="Absorbaid">Absorbaid</OPTION

<OPTION value="Abundance Marketing">Abundance Marketing</OPTION

<OPTION value="Accu Fitness">Accu Fitness</OPTION

<OPTION value="AchievOne">AchievOne</OPTION

<OPTION value="Action Labs">Action Labs</OPTION

<OPTION value="ActiPet">ActiPet</OPTION

<OPTION value="Adams Respiratory Therapeutics">Adams Respiratory Therapeutics</OPTION

<OPTION value="Advanced Muscle Science">Advanced Muscle Science</OPTION

<OPTION value="Advanced Sports Nutrition">Advanced Sports Nutrition</OPTION

<OPTION value="Agape Health Products">Agape Health Products</OPTION

<OPTION value="Alacer Corporation">Alacer Corporation</OPTION

<OPTION value="Alba Botanica">Alba Botanica</OPTION

<OPTION value="All Terrain">All Terrain</OPTION

<OPTION value="AlliMax">AlliMax</OPTION

<OPTION value="ALR Industries">ALR Industries</OPTION

<OPTION value="Alta Health Products">Alta Health Products</OPTION

<OPTION value="Alvita">Alvita</OPTION

<OPTION value="Amazing Herbs">Amazing Herbs</OPTION

<OPTION value="American Biologics">American Biologics</OPTION

<OPTION value="American BioSciences">American BioSciences</OPTION

<OPTION value="American Biotech Labs">American Biotech Labs</OPTION

<OPTION value="American Health">American Health</OPTION

<OPTION value="Amerifit">Amerifit</OPTION

<OPTION value="Amino Vital">Amino Vital</OPTION

<OPTION value="Anabolic Xtreme">Anabolic Xtreme</OPTION

<OPTION value="Aoqili">Aoqili</OPTION

<OPTION value="Applied Nutrition">Applied Nutrition</OPTION

<OPTION value="Aqua Flora">Aqua Flora</OPTION

<OPTION value="Arizona Natural">Arizona Natural</OPTION

<OPTION value="Ark Naturals">Ark Naturals</OPTION

<OPTION value="Artemis Woman">Artemis Woman</OPTION

<OPTION value="AST Sports Science">AST Sports Science</OPTION

<OPTION value="At Last, Inc.">At Last, Inc.</OPTION

<OPTION value="Atkins">Atkins</OPTION

<OPTION value="Aura Cacia">Aura Cacia</OPTION

<OPTION value="Avalon Organics">Avalon Organics</OPTION

<OPTION value="Axis Labs">Axis Labs</OPTION

<OPTION value="Ayurceutics">Ayurceutics</OPTION

<OPTION value="Azure Cosmeceuticals">Azure Cosmeceuticals</OPTION

<OPTION value="Baby's Bliss">Baby's Bliss</OPTION

<OPTION value="Bach Flower Remedies">Bach Flower Remedies</OPTION

<OPTION value="Barmensen Labs">Barmensen Labs</OPTION

<OPTION value="Baywood">Baywood</OPTION

<OPTION value="Beano">Beano</OPTION

<OPTION value="Beauty Without Cruelty">Beauty Without Cruelty</OPTION

<OPTION value="Bella Lucy">Bella Lucy</OPTION

<OPTION value="Berkeley Premium Nutraceuticals">Berkeley Premium Nutraceuticals</OPTION

<OPTION value="Better Health">Better Health</OPTION

<OPTION value="Bhelliom Enterprises">Bhelliom Enterprises</OPTION

<OPTION value="Bio-Form Essentials">Bio-Form Essentials</OPTION

<OPTION value="Bio-Strath">Bio-Strath</OPTION

<OPTION value="Bio-Tech">Bio-Tech</OPTION

<OPTION value="Biochem Sports">Biochem Sports</OPTION

<OPTION value="Bioforce">Bioforce</OPTION

<OPTION value="Biomed Comm">Biomed Comm</OPTION

<OPTION value="BioNutraceuticals">BioNutraceuticals</OPTION

<OPTION value="BioNutritional Research Group">BioNutritional Research Group</OPTION

<OPTION value="BioQuest">BioQuest</OPTION

<OPTION value="Biosential">Biosential</OPTION

<OPTION value="Biotec">Biotec</OPTION

<OPTION value="Biotest Laboratories">Biotest Laboratories</OPTION

<OPTION value="Biotics Research Corp.">Biotics Research Corp.</OPTION

<OPTION value="Bliss by Mom">Bliss by Mom</OPTION

<OPTION value="Blue Spring">Blue Spring</OPTION

<OPTION value="BNG Enterprises">BNG Enterprises</OPTION

<OPTION value="Boericke and Tafel">Boericke and Tafel</OPTION

<OPTION value="Boiron">Boiron</OPTION

<OPTION value="Boland Naturals">Boland Naturals</OPTION

<OPTION value="Books on Health">Books on Health</OPTION

<OPTION value="Botanical Solutions">Botanical Solutions</OPTION

<OPTION value="Broadmoore Labs">Broadmoore Labs</OPTION

<OPTION value="Bronner">Bronner</OPTION

<OPTION value="BSN">BSN</OPTION

<OPTION value="Buried Treasure">Buried Treasure</OPTION

<OPTION value="Burt's Bees">Burt's Bees</OPTION

<OPTION value="Canker Sores Begone">Canker Sores Begone</OPTION

<OPTION value="Carb-Boom">Carb-Boom</OPTION

<OPTION value="Cardio Fire">Cardio Fire</OPTION

<OPTION value="Carlson Labs">Carlson Labs</OPTION

<OPTION value="Carter-Reed">Carter-Reed</OPTION

<OPTION value="Castiva">Castiva</OPTION

<OPTION value="Celestial Seasonings">Celestial Seasonings</OPTION

<OPTION value="Central Coast Nutraceuticals">Central Coast Nutraceuticals</OPTION

<OPTION value="Cerburg">Cerburg</OPTION

<OPTION value="Champion Nutrition">Champion Nutrition</OPTION

<OPTION value="Chandrika">Chandrika</OPTION

<OPTION value="Chaser">Chaser</OPTION

<OPTION value="ChildLife">ChildLife</OPTION

<OPTION value="China Mystique">China Mystique</OPTION

<OPTION value="CJ Distributors">CJ Distributors</OPTION

<OPTION value="Claritin">Claritin</OPTION

<OPTION value="Clear Products">Clear Products</OPTION

<OPTION value="Clif Bar">Clif Bar</OPTION

<OPTION value="CMI Nutrition">CMI Nutrition</OPTION

<OPTION value="Controlled Labs">Controlled Labs</OPTION

<OPTION value="Country Life">Country Life</OPTION

<OPTION value="CTD Labs">CTD Labs</OPTION

<OPTION value="Cuur">Cuur</OPTION

<OPTION value="Cytodyne Technologies">Cytodyne Technologies</OPTION

<OPTION value="CytoSport">CytoSport</OPTION

<OPTION value="D and E Pharmaceuticals">D and E Pharmaceuticals</OPTION

<OPTION value="Dancing Paws">Dancing Paws</OPTION

<OPTION value="Derma E">Derma E</OPTION

<OPTION value="Dermavant Labs">Dermavant Labs</OPTION

<OPTION value="Desert Essence">Desert Essence</OPTION

<OPTION value="Designer Supplements">Designer Supplements</OPTION

<OPTION value="Detoxify">Detoxify</OPTION

<OPTION value="Devine Distribution">Devine Distribution</OPTION

<OPTION value="Direct Marketing Concepts">Direct Marketing Concepts</OPTION

<OPTION value="Discovery Herbs">Discovery Herbs</OPTION

<OPTION value="Doctor's Best">Doctor's Best</OPTION

<OPTION value="Dr. Christophers">Dr. Christophers</OPTION

<OPTION value="Dr. Frank's">Dr. Frank's</OPTION

<OPTION value="Dymatize Nutrition">Dymatize Nutrition</OPTION

<OPTION value="Dynakor Pharmacal">Dynakor Pharmacal</OPTION

<OPTION value="Dynamic Health Laboratories">Dynamic Health Laboratories</OPTION

<OPTION value="Earth Science">Earth Science</OPTION

<OPTION value="Earthrise">Earthrise</OPTION

<OPTION value="EAS">EAS</OPTION

<OPTION value="Eclectic Products">Eclectic Products</OPTION

<OPTION value="Eclipse Sports Supplements">Eclipse Sports Supplements</OPTION

<OPTION value="Ecoland">Ecoland</OPTION

<OPTION value="Eden">Eden</OPTION

<OPTION value="EGOceutical">EGOceutical</OPTION

<OPTION value="Emerita">Emerita</OPTION

<OPTION value="Enzymatic Therapy">Enzymatic Therapy</OPTION

<OPTION value="Epic Nutrition">Epic Nutrition</OPTION

<OPTION value="ErgoPharm">ErgoPharm</OPTION

<OPTION value="ESSIAC Products">ESSIAC Products</OPTION

<OPTION value="Esteem">Esteem</OPTION

<OPTION value="Ethical Nutrients">Ethical Nutrients</OPTION

<OPTION value="eVitamins">eVitamins</OPTION

<OPTION value="Fearn">Fearn</OPTION

<OPTION value="First Organics">First Organics</OPTION

<OPTION value="Fizogen Precision Technologies">Fizogen Precision Technologies</OPTION

<OPTION value="Flax Z Snax">Flax Z Snax</OPTION

<OPTION value="Flora">Flora</OPTION

<OPTION value="Food Force">Food Force</OPTION

<OPTION value="Food Science of Vermont">Food Science of Vermont</OPTION

<OPTION value="Forward Foods">Forward Foods</OPTION

<OPTION value="Fountain of Youth">Fountain of Youth</OPTION

<OPTION value="Fresh Wave">Fresh Wave</OPTION

<OPTION value="FTH Nutraceuticals">FTH Nutraceuticals</OPTION

<OPTION value="Futurebiotics">Futurebiotics</OPTION

<OPTION value="Garden Greens">Garden Greens</OPTION

<OPTION value="Garden of Life">Garden of Life</OPTION

<OPTION value="Gaspari Nutrition">Gaspari Nutrition</OPTION

<OPTION value="Generation Plus">Generation Plus</OPTION

<OPTION value="Generix Laboratories">Generix Laboratories</OPTION

<OPTION value="Genesis Today">Genesis Today</OPTION

<OPTION value="Genisoy">Genisoy</OPTION

<OPTION value="German Amer. Tech.">German Amer. Tech.</OPTION

<OPTION value="GlaxoSmithKline">GlaxoSmithKline</OPTION

<OPTION value="Global Labs">Global Labs</OPTION

<OPTION value="Grandma Lucy's">Grandma Lucy's</OPTION

<OPTION value="Grandpa's">Grandpa's</OPTION

<OPTION value="Greek Island Labs">Greek Island Labs</OPTION

<OPTION value="Green Foods">Green Foods</OPTION

<OPTION value="Greens Today">Greens Today</OPTION

<OPTION value="H57">H57</OPTION

<OPTION value="Hain">Hain</OPTION

<OPTION value="Harmonic Innerprizes">Harmonic Innerprizes</OPTION

<OPTION value="Health From the Sun">Health From the Sun</OPTION

<OPTION value="Health Plus Inc.">Health Plus Inc.</OPTION

<OPTION value="Health Support">Health Support</OPTION

<OPTION value="HealthSmart Foods">HealthSmart Foods</OPTION

<OPTION value="Healthy Origins">Healthy Origins</OPTION

<OPTION value="Healthy Relief">Healthy Relief</OPTION

<OPTION value="Heaven And Earth">Heaven And Earth</OPTION

<OPTION value="Heaven Sent Naturals">Heaven Sent Naturals</OPTION

<OPTION value="Heel BHI for Homeopathy">Heel BHI for Homeopathy</OPTION

<OPTION value="Herb Pharm">Herb Pharm</OPTION

<OPTION value="Herbalife">Herbalife</OPTION

<OPTION value="Herbasway Lab">Herbasway Lab</OPTION

<OPTION value="Herbs for Kids">Herbs for Kids</OPTION

<OPTION value="Hero">Hero</OPTION

<OPTION value="Hi-Tech Pharmaceuticals">Hi-Tech Pharmaceuticals</OPTION

<OPTION value="Himalaya Herbal Healthcare">Himalaya Herbal Healthcare</OPTION

<OPTION value="Himalayan Institute">Himalayan Institute</OPTION

<OPTION value="Hobe Laboratories">Hobe Laboratories</OPTION

<OPTION value="Home Access">Home Access</OPTION

<OPTION value="Home Health Products">Home Health Products</OPTION

<OPTION value="Hot Stuff">Hot Stuff</OPTION

<OPTION value="Howard Naturals">Howard Naturals</OPTION

<OPTION value="Human Development">Human Development</OPTION

<OPTION value="Hyland's">Hyland's</OPTION

<OPTION value="I57 Ignite">I57 Ignite</OPTION

<OPTION value="IDS Sports">IDS Sports</OPTION

<OPTION value="Imperial Elixir">Imperial Elixir</OPTION

<OPTION value="Improvita">Improvita</OPTION

<OPTION value="Inholtra">Inholtra</OPTION

<OPTION value="Inner Armour">Inner Armour</OPTION

<OPTION value="Innovative Products">Innovative Products</OPTION

<OPTION value="Instone">Instone</OPTION

<OPTION value="ION Labs">ION Labs</OPTION

<OPTION value="Iovate Health Sciences">Iovate Health Sciences</OPTION

<OPTION value="Irwin Naturals">Irwin Naturals</OPTION

<OPTION value="iSatori Global Technologies">iSatori Global Technologies</OPTION

<OPTION value="ISS Research">ISS Research</OPTION

<OPTION value="Jan Tana">Jan Tana</OPTION

<OPTION value="Jarrow">Jarrow</OPTION

<OPTION value="Jason Natural Cosmetics">Jason Natural Cosmetics</OPTION

<OPTION value="Jason Winters">Jason Winters</OPTION

<OPTION value="Kal">Kal</OPTION

<OPTION value="Kay's Naturals">Kay's Naturals</OPTION

<OPTION value="Kcep Laboratories">Kcep Laboratories</OPTION

<OPTION value="Kemistry">Kemistry</OPTION

<OPTION value="Kendy USA">Kendy USA</OPTION

<OPTION value="KingBio Natural Medicine">KingBio Natural Medicine</OPTION

<OPTION value="Kiss My Face">Kiss My Face</OPTION

<OPTION value="Klein-Becker">Klein-Becker</OPTION

<OPTION value="KMS">KMS</OPTION

<OPTION value="Knight-McDowell Labs">Knight-McDowell Labs</OPTION

<OPTION value="Kolorex">Kolorex</OPTION

<OPTION value="Kroeger Herb">Kroeger Herb</OPTION

<OPTION value="Kyolic">Kyolic</OPTION

<OPTION value="L.A. Naturals">L.A. Naturals</OPTION

<OPTION value="Labrada Nutrition">Labrada Nutrition</OPTION

<OPTION value="Lamas Beauty">Lamas Beauty</OPTION

<OPTION value="Lane Labs">Lane Labs</OPTION

<OPTION value="Larenim Mineral Makeup">Larenim Mineral Makeup</OPTION

<OPTION value="Larrea Biosciences">Larrea Biosciences</OPTION

<OPTION value="Learner's Edge">Learner's Edge</OPTION

<OPTION value="Lexxus International">Lexxus International</OPTION

<OPTION value="LG Sciences">LG Sciences</OPTION

<OPTION value="Libido Edge">Libido Edge</OPTION

<OPTION value="Liddell Laboratories">Liddell Laboratories</OPTION

<OPTION value="Life Extension">Life Extension</OPTION

<OPTION value="Life-Flo">Life-Flo</OPTION

<OPTION value="Lily of the Desert">Lily of the Desert</OPTION

<OPTION value="Liquid Health">Liquid Health</OPTION

<OPTION value="Loanda Herbal Soaps">Loanda Herbal Soaps</OPTION

<OPTION value="Lucky Tiger">Lucky Tiger</OPTION

<OPTION value="Luna Bars">Luna Bars</OPTION

<OPTION value="M.D. Science Lab">M.D. Science Lab</OPTION

<OPTION value="Macro Life Naturals">Macro Life Naturals</OPTION

<OPTION value="Maitake Products Inc">Maitake Products Inc</OPTION

<OPTION value="Maritz Mayer">Maritz Mayer</OPTION

<OPTION value="Max Factor">Max Factor</OPTION

<OPTION value="Maximum Human Performance">Maximum Human Performance</OPTION

<OPTION value="Maximum International">Maximum International</OPTION

<OPTION value="Maximum Living">Maximum Living</OPTION

<OPTION value="Maximum Nutrients">Maximum Nutrients</OPTION

<OPTION value="Medi+Straw">Medi+Straw</OPTION

<OPTION value="Medical Futures Inc">Medical Futures Inc</OPTION

<OPTION value="MedSpan Laboratories">MedSpan Laboratories</OPTION

<OPTION value="MET-Rx">MET-Rx</OPTION

<OPTION value="Metabolic Response Modifiers">Metabolic Response Modifiers</OPTION

<OPTION value="Michael's">Michael's</OPTION

<OPTION value="Michelle's Miracle">Michelle's Miracle</OPTION

<OPTION value="Mill Creek">Mill Creek</OPTION

<OPTION value="MLO">MLO</OPTION

<OPTION value="MMUSA Muscle Marketing USA">MMUSA Muscle Marketing USA</OPTION

<OPTION value="ModuCare (EPI)">ModuCare (EPI)</OPTION

<OPTION value="Molecular Nutrition">Molecular Nutrition</OPTION

<OPTION value="Montana">Montana</OPTION

<OPTION value="Morter HealthSystem">Morter HealthSystem</OPTION

<OPTION value="Muscle Fortress">Muscle Fortress</OPTION

<OPTION value="MuscleTech">MuscleTech</OPTION

<OPTION value="MyoMed">MyoMed</OPTION

<OPTION value="Nasaline">Nasaline</OPTION

<OPTION value="National Health Products">National Health Products</OPTION

<OPTION value="Natra-Bio">Natra-Bio</OPTION

<OPTION value="Natracare">Natracare</OPTION

<OPTION value="Natren">Natren</OPTION

<OPTION value="Natrol">Natrol</OPTION

<OPTION value="Naturade">Naturade</OPTION

<OPTION value="Natural Balance">Natural Balance</OPTION

<OPTION value="Natural Care">Natural Care</OPTION

<OPTION value="Natural Miracles">Natural Miracles</OPTION

<OPTION value="Natural Pet Pharmaceuticals">Natural Pet Pharmaceuticals</OPTION

<OPTION value="Natural Product Solutions">Natural Product Solutions</OPTION

<OPTION value="Natural Sources">Natural Sources</OPTION

<OPTION value="Natural Sport">Natural Sport</OPTION

<OPTION value="Natural Vitality">Natural Vitality</OPTION

<OPTION value="Naturally">Naturally</OPTION

<OPTION value="NaturalMax">NaturalMax</OPTION

<OPTION value="Nature Works">Nature Works</OPTION

<OPTION value="Nature's Answer">Nature's Answer</OPTION

<OPTION value="Nature's Benefit">Nature's Benefit</OPTION

<OPTION value="Nature's Best">Nature's Best</OPTION

<OPTION value="Nature's Gate">Nature's Gate</OPTION

<OPTION value="Nature's Gift">Nature's Gift</OPTION

<OPTION value="Nature's Herbs">Nature's Herbs</OPTION

<OPTION value="Nature's Life">Nature's Life</OPTION

<OPTION value="Nature's Perfect">Nature's Perfect</OPTION

<OPTION value="Nature's Plus">Nature's Plus</OPTION

<OPTION value="Nature's Renewal">Nature's Renewal</OPTION

<OPTION value="Nature's Secret">Nature's Secret</OPTION

<OPTION value="Nature's Way">Nature's Way</OPTION

<OPTION value="NatureMost">NatureMost</OPTION

<OPTION value="Natures Harmony">Natures Harmony</OPTION

<OPTION value="New Wave Enviro">New Wave Enviro</OPTION

<OPTION value="NewChapter">NewChapter</OPTION

<OPTION value="Next Proteins">Next Proteins</OPTION

<OPTION value="Nirvana Natural">Nirvana Natural</OPTION

<OPTION value="Nordic Naturals">Nordic Naturals</OPTION

<OPTION value="North American Herb And Spice">North American Herb And Spice</OPTION

<OPTION value="Novogen">Novogen</OPTION

<OPTION value="Now">Now</OPTION

<OPTION value="NuAge Homeopathic Remedies">NuAge Homeopathic Remedies</OPTION

<OPTION value="Nutiva">Nutiva</OPTION

<OPTION value="Nutrabolics">Nutrabolics</OPTION

<OPTION value="NutraLab">NutraLab</OPTION

<OPTION value="NutraMax Laboratories">NutraMax Laboratories</OPTION

<OPTION value="Nutramerica">Nutramerica</OPTION

<OPTION value="Nutrapathic">Nutrapathic</OPTION

<OPTION value="NutraQuest. Inc.">NutraQuest. Inc.</OPTION

<OPTION value="Nutrex">Nutrex</OPTION

<OPTION value="Nutricology">Nutricology</OPTION

<OPTION value="Nutricor Labs">Nutricor Labs</OPTION

<OPTION value="Nutritech">Nutritech</OPTION

<OPTION value="Nutrition Now">Nutrition Now</OPTION

<OPTION value="Nutriworks">Nutriworks</OPTION

<OPTION value="NV Inc.">NV Inc.</OPTION

<OPTION value="NVE Pharmaceuticals">NVE Pharmaceuticals</OPTION

<OPTION value="Nx Labs">Nx Labs</OPTION

<OPTION value="Ola Loa">Ola Loa</OPTION

<OPTION value="Olympian Labs">Olympian Labs</OPTION

<OPTION value="Only Natural">Only Natural</OPTION

<OPTION value="Optimum Nutrition">Optimum Nutrition</OPTION

<OPTION value="Organic India">Organic India</OPTION

<OPTION value="OxyLife">OxyLife</OPTION

<OPTION value="Pacific Health">Pacific Health</OPTION

<OPTION value="Palo Alto Labs">Palo Alto Labs</OPTION

<OPTION value="Pbl">Pbl</OPTION

<OPTION value="Peaceful Mountain">Peaceful Mountain</OPTION

<OPTION value="PerCoBa">PerCoBa</OPTION

<OPTION value="Pet Aromatics">Pet Aromatics</OPTION

<OPTION value="Pet Naturals of Vermont">Pet Naturals of Vermont</OPTION

<OPTION value="PetMax Naturals">PetMax Naturals</OPTION

<OPTION value="PhytoPharmica®">PhytoPharmica®</OPTION

<OPTION value="Pines International">Pines International</OPTION

<OPTION value="Pinnacle">Pinnacle</OPTION

<OPTION value="Pioneer">Pioneer</OPTION

<OPTION value="Planetary Formulas">Planetary Formulas</OPTION

<OPTION value="Powerbar">Powerbar</OPTION

<OPTION value="Powerbutter">Powerbutter</OPTION

<OPTION value="Premier Marketing">Premier Marketing</OPTION

<OPTION value="Premier One">Premier One</OPTION

<OPTION value="Prevention">Prevention</OPTION

<OPTION value="Prilosec">Prilosec</OPTION

<OPTION value="PrimaForce">PrimaForce</OPTION

<OPTION value="Pro Tan">Pro Tan</OPTION

<OPTION value="Prolab Nutrition">Prolab Nutrition</OPTION

<OPTION value="Promax Nutrition">Promax Nutrition</OPTION

<OPTION value="Pronatura">Pronatura</OPTION

<OPTION value="Proper Nutrition">Proper Nutrition</OPTION

<OPTION value="Proto Foods">Proto Foods</OPTION

<OPTION value="Pure and Basic">Pure and Basic</OPTION

<OPTION value="Pure Essence Labs">Pure Essence Labs</OPTION

<OPTION value="Pure Fruit Technologies">Pure Fruit Technologies</OPTION

<OPTION value="Pure Planet">Pure Planet</OPTION

<OPTION value="Pure Source">Pure Source</OPTION

<OPTION value="Purest Colloids">Purest Colloids</OPTION

<OPTION value="Puriclean">Puriclean</OPTION

<OPTION value="Quality of Life">Quality of Life</OPTION

<OPTION value="Quantum">Quantum</OPTION

<OPTION value="Queen Helene">Queen Helene</OPTION

<OPTION value="R Garden">R Garden</OPTION

<OPTION value="Rachel Perry">Rachel Perry</OPTION

<OPTION value="Rainbow Light">Rainbow Light</OPTION

<OPTION value="Rand Research Labs">Rand Research Labs</OPTION

<OPTION value="Renew Life">Renew Life</OPTION

<OPTION value="Reviva Labs">Reviva Labs</OPTION

<OPTION value="Ridgecrest">Ridgecrest</OPTION

<OPTION value="RNY Group">RNY Group</OPTION

<OPTION value="Rodial">Rodial</OPTION

<OPTION value="Rogaine">Rogaine</OPTION

<OPTION value="San Nutrition">San Nutrition</OPTION

<OPTION value="Sanhelios">Sanhelios</OPTION

<OPTION value="Sante Active">Sante Active</OPTION

<OPTION value="Scandinavian Formulas">Scandinavian Formulas</OPTION

<OPTION value="Schiff">Schiff</OPTION

<OPTION value="SciFit">SciFit</OPTION

<OPTION value="SciTec Nutrition">SciTec Nutrition</OPTION

<OPTION value="Sedona Labs">Sedona Labs</OPTION

<OPTION value="ShiKai">ShiKai</OPTION

<OPTION value="Silver Lake Research">Silver Lake Research</OPTION

<OPTION value="Similasan">Similasan</OPTION

<OPTION value="Size 0 Labs">Size 0 Labs</OPTION

<OPTION value="Slimage">Slimage</OPTION

<OPTION value="SlimQuick Laboratories">SlimQuick Laboratories</OPTION

<OPTION value="SmartBurn">SmartBurn</OPTION

<OPTION value="Smith Sorensen">Smith Sorensen</OPTION

<OPTION value="SNAC">SNAC</OPTION

<OPTION value="Solaray">Solaray</OPTION

<OPTION value="SolarChem Labs">SolarChem Labs</OPTION

<OPTION value="Solgar">Solgar</OPTION

<OPTION value="Source Naturals">Source Naturals</OPTION

<OPTION value="South Pacific Trading">South Pacific Trading</OPTION

<OPTION value="Spectrum">Spectrum</OPTION

<OPTION value="Spirit Sciences USA">Spirit Sciences USA</OPTION

<OPTION value="St. Paul Brands">St. Paul Brands</OPTION

<OPTION value="Stakich, Inc">Stakich, Inc</OPTION

<OPTION value="StarChem Labs">StarChem Labs</OPTION

<OPTION value="Sterling-Grant Laboratories">Sterling-Grant Laboratories</OPTION

<OPTION value="Sunny Green">Sunny Green</OPTION

<OPTION value="Superior Source">Superior Source</OPTION

<OPTION value="Supplement Training Systems">Supplement Training Systems</OPTION

<OPTION value="Symbiotics">Symbiotics</OPTION

<OPTION value="Syntrax">Syntrax</OPTION

<OPTION value="Teeccino">Teeccino</OPTION

<OPTION value="TestMedica">TestMedica</OPTION

<OPTION value="The Magic Pill Inc">The Magic Pill Inc</OPTION

<OPTION value="The Nutrition Farm">The Nutrition Farm</OPTION

<OPTION value="The Real Food Trading Company">The Real Food Trading Company</OPTION

<OPTION value="The Synergy Company">The Synergy Company</OPTION

<OPTION value="Thermolife">Thermolife</OPTION

<OPTION value="Thompson">Thompson</OPTION

<OPTION value="Thunder Ridge">Thunder Ridge</OPTION

<OPTION value="Thursday Plantation">Thursday Plantation</OPTION

<OPTION value="Tiger's Milk">Tiger's Milk</OPTION

<OPTION value="Tom's of Maine">Tom's of Maine</OPTION

<OPTION value="Traditional Medicinals">Traditional Medicinals</OPTION

<OPTION value="Tri-O-Plex">Tri-O-Plex</OPTION

<OPTION value="TriMedica">TriMedica</OPTION

<OPTION value="TriPharma">TriPharma</OPTION

<OPTION value="Trojan">Trojan</OPTION

<OPTION value="Tropical Oasis">Tropical Oasis</OPTION

<OPTION value="Twinlab">Twinlab</OPTION

<OPTION value="Tyler Encapsulations">Tyler Encapsulations</OPTION

<OPTION value="UAS Labs">UAS Labs</OPTION

<OPTION value="Ultimate Nutrition">Ultimate Nutrition</OPTION

<OPTION value="Ultralab Nutrition">Ultralab Nutrition</OPTION

<OPTION value="Universal Nutrition">Universal Nutrition</OPTION

<OPTION value="Urban Biologics">Urban Biologics</OPTION

<OPTION value="Valeo Fitness Gear">Valeo Fitness Gear</OPTION

<OPTION value="VegLife">VegLife</OPTION

<OPTION value="Viridis Laboratories">Viridis Laboratories</OPTION

<OPTION value="Vital Basics">Vital Basics</OPTION

<OPTION value="VitaLabs">VitaLabs</OPTION

<OPTION value="Vitaline Formulas">Vitaline Formulas</OPTION

<OPTION value="Vitanica">Vitanica</OPTION

<OPTION value="Vitol">Vitol</OPTION

<OPTION value="VPX">VPX</OPTION

<OPTION value="Vyotech">Vyotech</OPTION

<OPTION value="Wally's">Wally's</OPTION

<OPTION value="Weider">Weider</OPTION

<OPTION value="Weil">Weil</OPTION

<OPTION value="Weleda">Weleda</OPTION

<OPTION value="Wellements">Wellements</OPTION

<OPTION value="Window Rock">Window Rock</OPTION

<OPTION value="Wisdom of the Ancients">Wisdom of the Ancients</OPTION

<OPTION value="World Nutrition">World Nutrition</OPTION

<OPTION value="World Organic">World Organic</OPTION

<OPTION value="Wuyi Rock Tea">Wuyi Rock Tea</OPTION

<OPTION value="Xyience">Xyience</OPTION

<OPTION value="Yerba Prima">Yerba Prima</OPTION

<OPTION value="Yogi Tea Organic Teas">Yogi Tea Organic Teas</OPTION

<OPTION value="Youthful Essentials">Youthful Essentials</OPTION

<OPTION value="Zand">Zand</OPTION

<OPTION value="ZenCore">ZenCore</OPTION

<OPTION value="Zenergize">Zenergize</OPTION

<OPTION value="Zicam">Zicam</OPTION

<OPTION value="Zoller Labratories">Zoller Labratories</OPTION

<OPTION value="Zone Perfect">Zone Perfect</OPTION
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

<b> Products, Supplements, & Vitamins</b><br><br>

Error!
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
Last Updated: June 17, 2008<br>
Copyright &copy 2004 - <a href="http://www.evitamins1.com">eVitamins1.com</A>
</font>
</center>
</body>
</html>

---

### Post by MacAnthony on 2008-06-18
I think I know what the issue is, but just want to make sure I'm understanding.

It looks like the page is executing just fine, but what you are concerned with is the line that says 'Error!', Right?

---

### Post by CrusaderAD on 2008-06-18
Yes. The resulting page should show the products for the brand selected in the form. But instead it shows the error and nothing else. Which is bizarre because it works on the local server, but not this one.

---

### Post by MacAnthony on 2008-06-18
So the "problem" is in this block of code:

```

$sql = "SELECT *
FROM evitamins_products
WHERE brand='$brandname'
";
if(mysql_num_rows(mysql_query($sql)) < 1){
echo "Error!";
}

// Get Products Within The Category Below
$result = mysql_query("select * from evitamins_products WHERE brand='$brandname' ORDER by brand ASC LIMIT $start, $limit") or die (mysql_error());
while ($row = mysql_fetch_array($result))
{
include("show-thumbnail.php");
}

```

The problem as I see it is that it is running these queries using the variable $brandname but when the page first loads, brandname is set to null if there is no get line variable setting it (which I am assuming is the case). So the query is executing and returning 0 results.

What value should it be using for that query if one isn't set?

---

### Post by CrusaderAD on 2008-06-18
The way I am defining the variables is:

$brandname = (isset($_GET['brandname'])) ? $_GET['brandname']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;

But since I am using a form, should I be using $_FORM? Should I be defining a range of values or something?

---

### Post by MacAnthony on 2008-06-18
There is no global variable for $_FORM. If it's in the url, then you use a get global ($_GET), if the action to the form is set to POST you use ($_POST), if it can be passed by either a get variable or a post variable you would access it from ($_REQUEST). It all depends on how the value is being passed to the page (there is also a $_COOKIE and a $_SESSION).

---

### Post by CrusaderAD on 2008-06-19
The action of the form refers to "brand.php" which I'm sure you saw already... I'll try a few things... I am however getting this error too:

<errorentry>
	<datetime>2008-06-18 14:55:56 (EDT)</datetime>
	<errornum>8</errornum>
	<errortype>Notice</errortype>
	<errormsg>Use of undefined constant description - assumed 'description'</errormsg>
	<scriptname>/home/evitamins/websites/evitamins1/teststore/show-thumbnail.php</scriptname>
	<scriptlinenum>3</scriptlinenum>
</errorentry>

The page I would be pulling up uses this script. But it works fine if I just bring up brand.php and not use the form. I'll try a few things.

---

### Post by CrusaderAD on 2008-06-19
_REQUEST solved it. Thanks for all your help!

---

### Post by MacAnthony on 2008-06-19
The undefined constant is the issue I posted before where strings are properly enclosed in quotes so they appear to php to be constants. A bad habit that will cause unintented issues.

---

### Post by CrusaderAD on 2008-06-19
One last thing is buggin me. I have a header:

<H1 align=center>Vitamins & Supplements Made By <? echo $brandname; ?></H1>
<H2 align=center><? echo $brandname; ?> Supplements & Vitamins</H2>

which does not put the brand name into the page. It shows it fine if I do not use the form, but when I use the form, it doesn't show up. The strange thing is that it will show this:

<b><? echo $brandname; ?> Products, Supplements, & Vitamins</b><br><br>

Just beneath the header when I use the form. What's the problem?

---

### Post by MacAnthony on 2008-06-19
THe only thing that should cause that would be if there was some code modifying $brandname between the heading and the bolded lines beneath it. Seems odd that it would work sometimes though. Would you mind posting the full source again since it seems it's changed a bit since the original post?

---

### Post by CrusaderAD on 2008-06-19
Here's the source page:


<?
include("config.php");
include("error.php");

$brandname = (isset($_GET['brandname'])) ? $_GET['brandname']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;

?>

<html>
<head>
<title>Vitamins & Supplements Made By <? echo $brandname; ?></title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<META NAME="description" CONTENT="<? echo $brandname; ?> health vitamins and supplements.">
<META NAME="keywords" CONTENT="<? echo $brandname; ?>">
<meta name="Language" content="en">
<meta name="Distribution" content="global">
<meta name="author" content="<? echo $brandname; ?>">
<META NAME="robots" CONTENT="index,follow">

<? include("style.php"); ?>

</head>

<body topmargin="15" bgcolor=#ffffff>

<H1 align=center>Vitamins & Supplements Made By <? echo $brandname; ?></H1>
<H2 align=center><? echo $brandname; ?> Supplements & Vitamins</H2>

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

<b><? echo $brandname; ?> Products, Supplements, & Vitamins</b><br><br>

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
        WHERE brand='$brandname'
	   ";
if(mysql_num_rows(mysql_query($sql)) < 1){
echo "Error!";
}

// Get Products Within The Category Below
$result = mysql_query("select * from evitamins_products WHERE brand='$brandname' ORDER by brand ASC LIMIT $start, $limit") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{
include("show-thumbnail.php");
}

$prv = ($start-$limit);
$nxt = ($start+$limit);
if($prv < 0){
$previous = "";
}else {
$previous = "<a href=\"brand.php?brandname=$bran2&start=$prv&limit=$limit\"><<< Previous $limit Products From $brand2</a>";
}
if(mysql_num_rows(mysql_query($sql)) < $nxt){
$next = "";
}else {
$next = "<a href=\"brand.php?brandname=$brand2&start=$nxt&limit=$limit\">Next $limit Products From $brand2 >>></a>";
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

### Post by MacAnthony on 2008-06-19
I would move the line:
<b><? echo $brandname; ?> Products, Supplements, & Vitamins</b><br><br>

To be directly below

<H1 align=center>Vitamins & Supplements Made By <? echo $brandname; ?></H1>
<H2 align=center><? echo $brandname; ?> Supplements & Vitamins</H2>

Just for testing purposes. If it acts the same as the heading lines, then I would have to assume that one of the included files between those 2 blocks of code is altering the $brandname variable. So somewhere in either: "categories-drop-down.php", "brands-drop-down.php", "search-box.php", or "categories-listed.php" is likely the cause of your issue. I would either move the bold line or comment out each include to figure out which is causing the issue.

---

### Post by CrusaderAD on 2008-06-19
That did it. On the main page I had _GET for the variable instead of _REQUEST... THANKS AGAIN!

---

### Post by MacAnthony on 2008-06-19
NP, Glad you got it working.

---

