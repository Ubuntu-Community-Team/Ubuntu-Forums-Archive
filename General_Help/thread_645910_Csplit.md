---
title: "Csplit"
date: 2007-12-20
forum: General Help
---

### Post by KarateCowboy on 2007-12-20
Hi guys.  I am pulling my hair out over csplit.

I have a backup of a database made using mysql-admin and would like to extract the table definitions from it using csplit.  I want to go and start with "CREATE TABLE" and end with the next semicolon which should be the end of the table declaration. The command I am using is 
```

csplit backup_20071219_1631.sql '%CREATE\ TABLE%' '/;$/+1
```

But this is not working. It would be satisfied with all the definitions in one file or in a separate file each, so long as they are separated from the megabytes of data inserts
For example a table dec could look like
CREATE TABLE `mydb`.`mytablet` (
`AssessmentID` int(10) unsigned NOT NULL,
`ProgramID` int(10) unsigned NOT NULL,
`CreatorID` int(10) unsigned NOT NULL,
`LastUpdatedOn` datetime default NULL,
`LastUpdatedBy` int(10) unsigned default NULL,
PRIMARY KEY (`AssessmentID`),
KEY `FK_ndm_assessment_1` (`ProgramID`),
CONSTRAINT `FK_ndm_assessment_1` FOREIGN KEY (`ProgramID`) REFERENCES `ndm_program` (`ProgramID`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

---

