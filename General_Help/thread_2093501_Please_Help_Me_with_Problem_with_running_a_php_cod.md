---
title: "Please Help Me with Problem with running a php code in ubuntu!"
date: 2012-12-10
forum: General Help
---

### Post by bignixs on 2012-12-10
**I am trying to run the following code:**

[PHP]
$con = mysql_connect("localhost","db_user","abc123");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("db_name", $con);

$productid2 = $this->product->id;


$thename = mysql_query("SELECT * FROM pshop_product_lang WHERE id_product = '$productid2' LIMIT 1");

$thename2 = mysql_fetch_array($thename);

   
$string2 = $thename2['name'];

$string = (strlen($string2) > 25) ? substr($string2, 0, 25) . '...' : $string2;

$font  = 4;
$width  = imagefontwidth($font) * strlen($string);
$height = imagefontheight($font);

$image = imagecreatetruecolor ($width,$height);
$white = imagecolorallocate ($image,255,255,255);
$black = imagecolorallocate ($image,0,0,0);
imagefill($image,0,0,$white);

imagestring ($image,$font,0,0,$string, $black);

imagepng ($image, 'widgets/' . $productid2 . '-text.png');
[/PHP]

It works fine on my other server that is not using ubuntu, so I know the code is valid.

**I get this error:**

No such file found at "widgets/image-name.png"

i have gd-library installed.

Help is much appreciated!

---

### Post by Kirk Schnable on 2012-12-13
> **bignixs said:**
> **I am trying to run the following code:**

[PHP]
imagepng ($image, 'widgets/' . $productid2 . '-text.png');
[/PHP]

**I get this error:**

No such file found at "widgets/image-name.png"



It looks to me like imagepng() is looking for the file "widgets/image-name.png". So make sure there is a folder called "widgets" in the same folder as the PHP script.  As I understand, imagepng() outputs a file, so just make sure the folder exists and that your PHP running user has permission to write there. 

[http://php.net/imagepng](http://php.net/imagepng)

---

### Post by sdowney717 on 2012-12-13
linux cares about upper lower case, windoes does not. Does it match?

---

### Post by tgalati4 on 2012-12-13
Also check the permissions and the owner:group on the widgets directory.  PHP can get picky about read/execute privilege and ownership for serving files.  Windows handles permissions differently than linux.

---

