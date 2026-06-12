---
title: "File error when download through php"
date: 2012-12-18
forum: General Help
---

### Post by idontcheat on 2012-12-18
Guys, we're on making our project which one of the features can upload and download files at the same time. I need you help with this. The problem is like this, when an account uploaded a file (e.g. document files, .txt, .docx .pdf) and another account downloaded it, upon opening that certain file, it seem like it was corrupted and the application who use to open it, wasn't able to open it. 

here is our code in php:
[B]these is for the upload, filename uploadToDB.php
[/B][PHP]
<?php
       include_once("connect.php");
        if(isset($_POST['cmdSubmit']) && $_FILES['userFile']['size'] > 0) {
            extract( $_POST );
            $fileName = $_FILES['userFile']['name'];
            $tmpName  = $_FILES['userFile']['tmp_name'];
            $fileSize = $_FILES['userFile']['size'];
            $fileType = $_FILES['userFile']['type'];
            
            $AddQuery = "INSERT INTO audit (Changes) VALUES ('$_POST[cmdSubmit]')";         
            mysql_query($AddQuery);
            
            $fp = fopen($tmpName, 'r');
            $content = fread($fp, filesize($tmpName));
            $content = addslashes($content);
            fclose($fp);
            
            if(!get_magic_quotes_gpc()) {
                $fileName = addslashes($fileName);
            }
            $dsn = 'mysql:dbname=es;host=127.0.0.1;port=3306';
            $user= 'root';
            $password='';
            
           try {
                $dbh = new PDO($dsn, $user, $password);

                $insertSQL = $dbh->prepare(
                        "INSERT INTO documents (subject, instructor, file_name, " .
                            "file_size, file_bytes, file_type, received) VALUES (?,?,?,?,?,?,SYSDATE())")
                        or die ($mysqli->error);

                $insertSQL->bindParam(1, $subj, PDO::PARAM_STR, 60);
                $insertSQL->bindParam(2, $instruct, PDO::PARAM_STR, 60);
                $insertSQL->bindParam(3, $fileName, PDO::PARAM_STR, 60);
                $insertSQL->bindParam(4, $fileSize, PDO::PARAM_INT, 60);
                $insertSQL->bindParam(5, $content, PDO::PARAM_STR, $fileSize);
                $insertSQL->bindParam(6, $fileType, PDO::PARAM_STR, 60);
                
                $insertSQL->execute() or die ("<p>Upload Error: $insertSQL->error</p>");
            } catch (PDOException $e) {
                die ('Connection failed: '.$e->getMessage());
            }
                
            echo "<br>File $fileName uploaded<br>";
        }
        ?>[/PHP][B]code for download, filename download.php

[/B][PHP]<?php

$fileId = $_GET["fileId"];
$sql = "SELECT file_type, file_name, file_size, file_bytes FROM documents WHERE file_id = ?";
 $dsn = 'mysql:dbname=es;host=127.0.0.1;port=3306';
            $user= 'root';
            $password='';
try {
$dbh = new PDO($dsn, $user, $password);

$start = $dbh->prepare($sql) or die (implode(":", $start->errorInfo()));
$start->bindParam(1, $fileId, PDO::PARAM_INT, 40);
$start->execute() or die (implode(":", $start->errorInfo()));
$cols = $start->columnCount();

$row = $start->fetch();
header("Content-type: $row[0]");
header("Content-length: $row[2]");
header("Content-disposition: attachment; filename=$row[1]");
print $row[3];   

} catch (PDOException $e){
    die ('Connection failed:  '.$e->getMessage());
}

?>
    
[/PHP]I hope you guys can help us.
God speed!;)

---

