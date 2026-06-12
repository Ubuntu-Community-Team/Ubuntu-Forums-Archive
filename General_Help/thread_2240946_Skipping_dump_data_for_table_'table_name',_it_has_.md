---
title: "Skipping dump data for table 'table_name', it has no fields"
date: 2014-08-23
forum: General Help
---

### Post by JdeS on 2014-08-23
I recently upgraded to 14.04 and struggling with a SSH port forwarding / mysqldump issue.

The script I normally use to 'download' my databases from my remote servers has been failing when run on this machine (Ubuntu 14.04). The script was written many years ago, and even works today with my other machines (running on Fedora and CentOS).

Very quickly, I create a SSH connection for the port forwarding, something like:
```
ssh -vNL 33066:localhost:3306 jenia.example.com
```

With the mysql client, I can connect to the remote server, and run any query as expected.

However when I run mysqldump, say like this, it fails:
```
mysqldump --verbose --user=jdes --port=33066 --host=127.0.0.1 --password mydbname > ~/test.2014.08.23-05.sql
```

In the terminal window, this is what is returned:
```

-- Connecting to 127.0.0.1...
-- Retrieving table structure for table table_name_1...
-- Skipping dump data for table 'table_name_1', it has no fields

```

Meanwhile, in the (output) file, this is what is written:
```

-- MySQL dump 10.13  Distrib 5.5.38, for debian-linux-gnu (i686)
--
-- Host: 127.0.0.1    Database: mydbname
-- ------------------------------------------------------
-- Server version	5.1.73


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

```

---

