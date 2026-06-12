---
title: "not sure how to do this, get json value in .sh"
date: 2015-08-23
forum: General Help
---

### Post by matthew_smith2 on 2015-08-23
I am getting a json value returned from a curl request.  I need to get one value(the value of "SpotInstanceRequestId") from what was returned.  How would I go about this?  Is there some type of json interpreter, or would I have to use some other scripting.  Not sure what to do.  Here is the json:
```
{   "SpotInstanceRequests": [     {       "Status": {         "UpdateTime": "2014-04-30T18:16:21.000Z",         "Code": "fulfilled",         "Message": "Your Spot request is fulfilled."       },       "ProductDescription": "Linux/UNIX",       "InstanceId": "i-20170a7c",       "SpotInstanceRequestId": "sir-08b93456",       "State": "active",       "LaunchedAvailabilityZone": "us-west-1b",       "LaunchSpecification": {         "ImageId": "ami-7aba833f",         "KeyName": "May14Key",         "BlockDeviceMappings": [           {             "DeviceName": "/dev/sda1",             "Ebs": {               "DeleteOnTermination": true,               "VolumeType": "standard",               "VolumeSize": 8             }           }         ],         "EbsOptimized": false,         "SecurityGroups": [           {             "GroupName": "launch-wizard-1",             "GroupId": "sg-e38f24a7"           }         ],         "InstanceType": "m1.small"       },       "Type": "one-time",       "CreateTime": "2014-04-30T18:14:55.000Z",       "SpotPrice": "0.010000"     },     {       "Status": {         "UpdateTime": "2014-04-30T18:16:21.000Z",         "Code": "fulfilled",         "Message": "Your Spot request is fulfilled."       },       "ProductDescription": "Linux/UNIX",       "InstanceId": "i-894f53d5",       "SpotInstanceRequestId": "sir-285b1e56",       "State": "active",       "LaunchedAvailabilityZone": "us-west-1b",       "LaunchSpecification": {         "ImageId": "ami-7aba833f",         "KeyName": "May14Key",         "BlockDeviceMappings": [           {             "DeviceName": "/dev/sda1",             "Ebs": {               "DeleteOnTermination": true,               "VolumeType": "standard",               "VolumeSize": 8             }           }         ],         "EbsOptimized": false,         "SecurityGroups": [           {             "GroupName": "launch-wizard-1",             "GroupId": "sg-e38f24a7"           }         ],         "InstanceType": "m1.small"       },       "Type": "one-time",       "CreateTime": "2014-04-30T18:14:55.000Z",       "SpotPrice": "0.010000"     }   ] }
```

Edit:  Sorry, the json formatting is of for some reason.

---

### Post by TheFu on 2015-08-24
Pretty much all other scripting languages have json libraries to parse it.  When a script gets that complex, I switch from bash to perl, but ruby or python will handle json easily too.  I wouldn't fight with it under bash.

There may be a bash function that someone wrote to handle parsing json - did google find anything? 
[https://unix.stackexchange.com/questions/121718/how-to-parse-json-with-shell-scripting-in-linux](https://unix.stackexchange.com/questions/121718/how-to-parse-json-with-shell-scripting-in-linux) seems to make the same suggestion I did.

---

### Post by Habitual on 2015-08-24
Boto over python can do this.
so can  [ec2-describe-spot-instance-requests]("http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-spot-instance-requests.html")

---

### Post by Lars Noodén on 2015-08-24
I'd also reach for perl.

```

#!/usr/bin/perl                                                                                                       

use JSON;
use File::Slurp;

use strict;
use warnings;

my $filename = shift || '/dev/stdin';    	# get file name or stdin                                                

my $json_text = read_file($filename);   # entire file in scalar                                                       

my $json = decode_json $json_text;	# json as a data structure                                                    

foreach my $SpotInstanceRequests ( $json->{SpotInstanceRequests} ) {

    foreach my $req ( @{$SpotInstanceRequests} ) {
        print qq(SpotInstanceRequestId = ), $req->{SpotInstanceRequestId}, qq(\n);
    }

}

exit ( 0 );

```

The two modules are found in the repository as  *libfile-slurp-perl* and *libjson-perl*.

---

### Post by Lars Noodén on 2015-10-19
Just a follow up on File::Slurp.  It is apparently deprecated : [http://blogs.perl.org/users/leon_timmermans/2015/08/fileslurp-is-broken-and-wrong.html](http://blogs.perl.org/users/leon_timmermans/2015/08/fileslurp-is-broken-and-wrong.html)
The module File::Slurper should be used instead but it is not yet in the repository.

---

