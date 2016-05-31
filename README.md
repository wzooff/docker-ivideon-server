# Ivideon Server Headless (docker)

This image allows you to run ivideon headless server in container

For example
```
sudo docker run -d --name=CONTAINERNAME --net=host --log-driver=none -v /path/to/config/folder:/opt/ivideon/data wzooff/ivideon-server-headless
```
In specified folder you should place config videoserverd.conf with next content
```json
{
   "archive" : {
      "maxEventLogSize" : 20480,
      "path" : "/opt/ivideon/data/archive",
      "sizeLimit" : 102400,
      "sizeToCleanup" : 512,
      "useArchive" : true,
      "webcamBitRate" : 2048,
      "webcamFrameRate" : 5,
      "webcamVideoFormat" : 1
   },
   "cameras" : [
      {
         "id" : 1,
         "mdSensitivity" : 50,
         "name" : "cam1",
         "recordType" : "motion",
         "rtspTransport" : "tcp",
         "urlHigh" : "rtsp://admin:admin@ip/media/video1",
         "useCameraMotionDetector" : false,
         "useSound" : true
      }
   ],
   "localView" : {
      "passwordHash" : "md5hash_of_pw",
      "proxyPort" : 3101,
      "streamerPort" : 8080
   },
   "logging" : {
      "isTruncate" : false,
      "path" : "/dev/null",
      "rtspPath":"/dev/null"
   },
   "network" : {
      "ivideonProxyHost" : "proxy.ivideon.com"
   },
   "system" : {
      "cwd" : "/opt/ivideon/data"
   }
}
```
