---
title: "[SOLVED] Undefined index PHP"
date: 2008-06-17
forum: General Help
---

### Post by CrusaderAD on 2008-06-17
Hello. I am getting an error when running a script (it runs on another linux server with php4 just fine, but this is the server with the databases locally). The error is an Undefined index. Here is the log file:

<errorentry>
	<datetime>2008-06-17 13:03:16 (EDT)</datetime>
	<errornum>8</errornum>
	<errortype>Notice</errortype>
	<errormsg>Undefined index:  cid</errormsg>
	<scriptname>/home/evitamins/websites/evitamins1/teststore/category.php</scriptname>
	<scriptlinenum>7</scriptlinenum>
</errorentry>

<errorentry>
	<datetime>2008-06-17 13:03:16 (EDT)</datetime>
	<errornum>8</errornum>
	<errortype>Notice</errortype>
	<errormsg>Undefined index:  start</errormsg>
	<scriptname>/home/evitamins/websites/evitamins1/teststore/category.php</scriptname>
	<scriptlinenum>8</scriptlinenum>
</errorentry>

<errorentry>
	<datetime>2008-06-17 13:03:16 (EDT)</datetime>
	<errornum>8</errornum>
	<errortype>Notice</errortype>
	<errormsg>Undefined index:  limit</errormsg>
	<scriptname>/home/evitamins/websites/evitamins1/teststore/category.php</scriptname>
	<scriptlinenum>9</scriptlinenum>
</errorentry>

Here is the one part of the script I think is causing an issue:

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

I'm running this on Ubuntu Server 8.04 Hardy. Any help is appreciated!

---

### Post by LoneWolfJack on 2008-06-17
The lines of code you put there don't seem to be the one's the complaints are about. I'm pretty sure it's about register_globals again though.

---

### Post by CrusaderAD on 2008-06-17
Here's the lines where the error is pointing:

$cid = $_POST['cid'];
$start = $_POST['start'];
$limit = $_POST['limit'];

If there lines are not in the code, then I get a undefined variable error. Thanks!

---

### Post by kernelhaxor on 2008-06-17
can you post the html code of the form which posts to this page ?
the form is missing one of the fields: cid, start, limit .. or the fields are named differently

---

### Post by CrusaderAD on 2008-06-17
The page isn't using a form. What were basically doing it tapping into a sql database on another box. cid is a variable in the page. It works on the local box, but if you put if on a foreign box, it doesn't work. Here's the page:

<?
include("error.php");
include("config.php");

// Get Category Name Below For SE Optimizing

$cid = $_POST['cid'];
$start = $_POST['start'];
$limit = $_POST['limit'];

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

### Post by MacAnthony on 2008-06-17
The errors you are getting are just notices. They won't affect the running of the script. It's telling you that the indexes 'cid', 'start' and 'limit' aren't set for the variable $_POST.

Typically, you would want to check if they are set first.

```

$cid = (isset($_POST['cid'])) ? $_POST['cid']: null;
$start = (isset($_POST['start'])) ? $_POST['start'] : null;
$limit = (isset($_POST['limit'])) ? $_POST['limit'] : null;

```

That should get rid of the notices.

---

### Post by MacAnthony on 2008-06-17
We cross posted. Since it's not using a form and there aren't any POST variables, you should change the code to:

```

$cid = (isset($_GET['cid'])) ? $_GET['cid']: null;
$start = (isset($_GET['start'])) ? $_GET['start'] : null;
$limit = (isset($_GET['limit'])) ? $_GET['limit'] : null;

```

---

### Post by CrusaderAD on 2008-06-17
THANK YOU MacAnthony! Problem SOLVED.

---

