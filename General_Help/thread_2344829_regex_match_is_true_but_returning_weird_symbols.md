---
title: "regex match is true but returning weird symbols"
date: 2016-11-28
forum: General Help
---

### Post by i-z on 2016-11-28
I'm using boost 1.62 on ubuntu 16.04 LTS. 
I was using the same code and files on Scientific Linux 7.2 with boost 1.53 and it was working.

This is part of the code:

    boost::cmatch what ;
    const boost::regex exp ("(\\w+).txt",boost::regex::perl);
      if(boost::regex_match((*roc).second->getCalibrationFilePath().c_str(), what, exp, boost::match_extra))
            { 
               std::cout<<__PRETTY_FUNCTION__<< " (*roc).second->getCalibrationFilePath().c_str() " << (*roc).second->getCalibrationFilePath().c_str() << std::endl;
                std::cout<<__PRETTY_FUNCTION__<<     "what[1] " <<       what[1] << std::endl;
                std::cout<<__PRETTY_FUNCTION__<<     "exp " <<       exp << std::endl;
                calibrationFileRadix = what[1];
            }
            else
            {
                STDLINE("ERROR: Can't find the extension .txt in " + (*roc).second->getCalibrationFilePath(), ACRed);
                continue;
            }  

The file name that should match is something like /path/file_name.txt and I'd like to have file_name.txt as what[1].

The outputs that I get are: 

bool calibrationLoader::loadAllCalibrationFiles() (*roc).second->getCalibrationFilePath().c_str() CalGain_downstream_2016_04_05_3_0_4.txt

bool calibrationLoader::loadAllCalibrationFiles()what[1] pO&#65533;&#65533;&#65533;

bool calibrationLoader::loadAllCalibrationFiles()exp (\w+).txt

or 

bool calibrationLoader::loadAllCalibrationFiles() (*roc).second->getCalibrationFilePath().c_str() CalGain_downstream_2016_04_05_3_0_4.txt

bool calibrationLoader::loadAllCalibrationFiles()what[1] 

bool calibrationLoader::loadAllCalibrationFiles()exp (\w+).txt

I tested this regexp at [http://www.regextester.com/](http://www.regextester.com/) : it behaved as expected using (\w+).txt instead of (\\w+).txt

Thanks!

---

