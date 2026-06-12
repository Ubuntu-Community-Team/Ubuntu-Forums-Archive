---
title: "can't get sh script to work, problem with if statement"
date: 2015-09-08
forum: General Help
---

### Post by matthew_smith2 on 2015-09-08
I've looked at all the examples online, and I can't seem to get the if statement to work.  I have tried =, ==, even -eq.  I'm not sure what I am doing wrong, but the contents of the if statement are never executing.

Here is the portion I am having trouble with:

```
if [ "$amiid" == "$theamiid" ];
                      then
                        sfri=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestId")
                        temp="${sfri%\"}"
                        temp="${temp#\"}"
                        sfri="$temp"
                        aws ec2 cancel-spot-fleet-requests --spot-fleet-request-ids $sfri --terminate-instances
                        break
                    fi
```

Here is the whole thing, if you can spot any other problems.  I think I am ok though.

```
#!/bin/bash
PATH=/usr/local/bin:$PATH
sleep 1000
while true
  do

        file="/home/ubuntu/hc/testingsfr.restore"
        if [ ! -e "$file" ]; then
            
            theamiid="$(curl http://169.254.169.254/latest/meta-data/ami-id)"
            temp="\"$theamiid\""
            theamiid="$temp"
            
            aws ec2 describe-spot-fleet-requests > /home/ubuntu/hc/spot-fleet-requests.txt
            myarraylength=$(jq '.SpotFleetRequestConfigs | length' /home/ubuntu/hc/spot-fleet-requests.txt)
            
            
            for ((i=0;i < $myarraylength;i++))
                do
                    amiid=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestConfig.LaunchSpecifications[].ImageId")

                       if [ "$amiid" == "$theamiid" ];
                      then
                        sfri=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestId")
                        temp="${sfri%\"}"
                        temp="${temp#\"}"
                        sfri="$temp"
                        aws ec2 cancel-spot-fleet-requests --spot-fleet-request-ids $sfri --terminate-instances
                        break
                    fi
                done

        else

            aws s3 cp /home/ubuntu/hc/testingsfr-didit.txt s3://hashcat-turbo/watch/testingsfr-didit.txt
            aws s3 cp /home/ubuntu/hc/testingsfr.log s3://hashcat-turbo/testingsfr/testingsfr.log 
          
        fi

        sleep 250

  done
```

---

### Post by papibe on 2015-09-08
Hi matthew_smith2.

I don't understand some parts of your code, but I think I could give you some hints to debug it.

My first guess is that you have either spaces, newlines or other character you have to trim before comparing directly.

I would try this:
```
echo "theamiid"
echo "-----------------------------------------"
echo -n "$theamiid" | od -a
echo

echo "amiid"
echo "-----------------------------------------"
echo -n "$amiid" | od -a
echo

if [ "$amiid" == "$theamiid" ];
    ...
fi
```
Hope it helps. Let us know if that helped.
Regards.

---

### Post by ventrical on 2015-09-08
> **matthew_smith2 said:**
> I've looked at all the examples online, and I can't seem to get the if statement to work.  I have tried =, ==, even -eq.  I'm not sure what I am doing wrong, but the contents of the if statement are never executing.

Here is the portion I am having trouble with:

```
if [ "$amiid" == "$theamiid" ];
                      then
                        sfri=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestId")
                        temp="${sfri%\"}"
                        temp="${temp#\"}"
                        sfri="$temp"
                        aws ec2 cancel-spot-fleet-requests --spot-fleet-request-ids $sfri --terminate-instances
                        break
                    fi
```

Here is the whole thing, if you can spot any other problems.  I think I am ok though.

```
#!/bin/bash
PATH=/usr/local/bin:$PATH
sleep 1000
while true
  do

        file="/home/ubuntu/hc/testingsfr.restore"
        if [ ! -e "$file" ]; then
            
            theamiid="$(curl http://169.254.169.254/latest/meta-data/ami-id)"
            temp="\"$theamiid\""
            theamiid="$temp"
            
            aws ec2 describe-spot-fleet-requests > /home/ubuntu/hc/spot-fleet-requests.txt
            myarraylength=$(jq '.SpotFleetRequestConfigs | length' /home/ubuntu/hc/spot-fleet-requests.txt)
            
            
            for ((i=0;i < $myarraylength;i++))
                do
                    amiid=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestConfig.LaunchSpecifications[].ImageId")

                       if [ "$amiid" == "$theamiid" ];
                      then
                        sfri=$(cat /home/ubuntu/hc/spot-fleet-requests.txt | jq ".SpotFleetRequestConfigs[$i].SpotFleetRequestId")
                        temp="${sfri%\"}"
                        temp="${temp#\"}"
                        sfri="$temp"
                        aws ec2 cancel-spot-fleet-requests --spot-fleet-request-ids $sfri --terminate-instances
                        break
                    fi
                done
            else

            aws s3 cp /home/ubuntu/hc/testingsfr-didit.txt s3://hashcat-turbo/watch/testingsfr-didit.txt
            aws s3 cp /home/ubuntu/hc/testingsfr.log s3://hashcat-turbo/testingsfr/testingsfr.log 
          
        fi

        sleep 250

  done
```

Gee .. it's been a long time (and no too familar with this language) but when I used to program in Vax Unix all the commands had to be tight. I notice right away you have a hanging *else* ( a line space between 'done' and 'else'. Ive tightened it up for you. These were the rules in 1990. Not sure it applies here :)

Regards..

---

