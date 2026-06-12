---
title: "Help to getting data from simple website into MySQL dB"
date: 2019-05-24
forum: General Help
---

### Post by nissen on 2019-05-24
Hi, 

My setup:
Ubuntu 18.04
Apache2 
PHP 
MySQL
phpMyAdmin

I have created a simple website with one field (text) and one button to send the input text to the database behind. It's a .php file 

I have created a database and a table using phpMyAdmin.

I can't figure out how to create connection between my simple website and the database so when I hit "send" the data is being send to the database. 

Simple website
form.php:
[PHP]
<form method="POST" action"connectdb.php">
Input: <input type="text" name="input"></p>
<input type"submit" value"Submit">
[/PHP]

connectdb.php:
[PHP]
$servername = "localhost";
$username = "root";
$password = "hestevogn";
$database = "nemDB";

// Create connection
$conn = new mysqli($servername, $username, $password, $database);

// Check connection
if($conn->connect_error) {
die("Connection failed: ". $conn->connect_error);}
echo "Connection successful";
[/PHP]

When I run connectdb.php I get "Connection successful" and when I edit database name I get "Connection failed" so I quite sure that I have connected properbly to database named nemDB. The problem is how do I get data into the database through my website. 

It's my first time setting up and using the LAMP-stack so please no advanced explanations :)

---

### Post by SeijiSensei on 2019-05-24
All the data is stored in the $_POST special array.  You would need to iterate over it and build an insert query.  

Long ago, I wrote functions to handle database tasks.  Here's the one to insert data from an array into a (PostgreSQL) database.  You need to make a few edits to make it work with MySQL.

```

    function db_insert($conn,$table,$input_array) {

        # insert a record into $table using connection $conn
        # all values in $input_array with keys that match
        # fieldnames will be inserted

        $get_types=pg_Exec($conn,"select * from $table limit 1;");
        $nf=pg_NumFields($get_types);

        $vars="";
        $vals="";

        # traverse the fields looking for fieldnames
        # that match an index in $input_array

        for ($i=0; $i<$nf; $i++) {

            $type=pg_FieldType($get_types,$i);
            $name=pg_FieldName($get_types,$i);

            # ignore fields without matching input key
            if (!isset($input_array[$name])) {
                continue;
            } else {
                $value=$input_array[$name];
            }

            # handler for null entries ($input_array[$field]='')
            # postgres allows set var=null statements
            if (empty($value) && !is_numeric($value)) {
                $value="null";
            }

            # coerce values if appropriate
            if ($type=="bool" && ($value || $value="true" || $value="True" ||
                                  $value=="t" || $value=="T" || $value=="Y")) {
                $value='t';
            }  else if ($type=="bool") {
                $value='f';
            }

            # escape any quotes in text fields with double quotes
            if (preg_match("/char/i",$type) || preg_match("/text/i",$type)) {
                if ($value=="null") {
                    $value="''";

                } else if (strstr($value,"'")) {
                    $value="'".str_replace("'","''",trim($value))."'";

                } else {
                    $value="'".trim($value)."'";
                }
            }

            # build the insert query lists
            $vars .= $name.",";
            $vals .= $value.",";

        }

        # lop off trailing commas and compose the insert query
        $query="insert into $table (".substr($vars,0,-1).") values(".substr($vals,0,-1).");";
        $insert=@pg_Exec($conn,$query);

        return $insert;

    }

```

So if I had this function defined in my code (I maintain a PHP class that I require() in every script), I could run the command:

```

$myinsert=db_insert($conn,$sometablename,$_POST);

```

and the contents of the $_POST array would be searched for matching keys and the associated values stored in $sometablename in the database.

PHP comes with its own libraries of functions to handle tasks like this called [PEAR]("https://pear.php.net/manual/en/about.pear.php").  (These came out after I wrote my own functions.)  Here is the function to insert data: [https://pear.php.net/manual/en/package.database.db-dataobject.db-dataobject.insert.php](https://pear.php.net/manual/en/package.database.db-dataobject.db-dataobject.insert.php)

Writing PHP scripts from scratch that use a database like MySQL often requires you to have at least a basic knowledge of SQL.

---

### Post by nissen on 2019-05-25
> **SeijiSensei said:**
> All the data is stored in the $_POST special array.  You would need to iterate over it and build an insert query.  

Long ago, I wrote functions to handle database tasks.  Here's the one to insert data from an array into a (PostgreSQL) database.  You need to make a few edits to make it work with MySQL.

```

    function db_insert($conn,$table,$input_array) {

        # insert a record into $table using connection $conn
        # all values in $input_array with keys that match
        # fieldnames will be inserted

        $get_types=pg_Exec($conn,"select * from $table limit 1;");
        $nf=pg_NumFields($get_types);

        $vars="";
        $vals="";

        # traverse the fields looking for fieldnames
        # that match an index in $input_array

        for ($i=0; $i<$nf; $i++) {

            $type=pg_FieldType($get_types,$i);
            $name=pg_FieldName($get_types,$i);

            # ignore fields without matching input key
            if (!isset($input_array[$name])) {
                continue;
            } else {
                $value=$input_array[$name];
            }

            # handler for null entries ($input_array[$field]='')
            # postgres allows set var=null statements
            if (empty($value) && !is_numeric($value)) {
                $value="null";
            }

            # coerce values if appropriate
            if ($type=="bool" && ($value || $value="true" || $value="True" ||
                                  $value=="t" || $value=="T" || $value=="Y")) {
                $value='t';
            }  else if ($type=="bool") {
                $value='f';
            }

            # escape any quotes in text fields with double quotes
            if (preg_match("/char/i",$type) || preg_match("/text/i",$type)) {
                if ($value=="null") {
                    $value="''";

                } else if (strstr($value,"'")) {
                    $value="'".str_replace("'","''",trim($value))."'";

                } else {
                    $value="'".trim($value)."'";
                }
            }

            # build the insert query lists
            $vars .= $name.",";
            $vals .= $value.",";

        }

        # lop off trailing commas and compose the insert query
        $query="insert into $table (".substr($vars,0,-1).") values(".substr($vals,0,-1).");";
        $insert=@pg_Exec($conn,$query);

        return $insert;

    }

```

So if I had this function defined in my code (I maintain a PHP class that I require() in every script), I could run the command:

```

$myinsert=db_insert($conn,$sometablename,$_POST);

```

and the contents of the $_POST array would be searched for matching keys and the associated values stored in $sometablename in the database.

PHP comes with its own libraries of functions to handle tasks like this called [PEAR]("https://pear.php.net/manual/en/about.pear.php").  (These came out after I wrote my own functions.)  Here is the function to insert data: [https://pear.php.net/manual/en/package.database.db-dataobject.db-dataobject.insert.php](https://pear.php.net/manual/en/package.database.db-dataobject.db-dataobject.insert.php)

Writing PHP scripts from scratch that use a database like MySQL often requires you to have at least a basic knowledge of SQL.

Thank you for your reply. 

It is more advanced than I level. I think I need to get some basic knowledge about MySQL first as you mentioned :)

---

### Post by oldos2er on 2019-05-27
Moved to General Help.

---

