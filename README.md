# HLS encryption prototype (AES-128 based)

## Try to setup
### BACKEND
First of all you need to create an encryption key `enc.key` by using the following command:
```sh
openssl rand 16 > enc.key
``` 
then create `keyinfo` file
and it should be in this format:
```
link_of_enc.key
key_file_path
IV (optional)
```
for example
```
http://127.0.0.1:8080/enc.key
enc.key
```

and add your video in `./database`

run the following command to create the encrypted video
```sh
ffmpeg -y
  -i './database/{{ your video name }}'
  -hls_time 200
  -hls_key_info_file enc.keyinfo
  -hls_playlist_type vod
  -hls_segment_filename "./d/chunk-%d.ts"
  ./d/test.m3u8
```
### FRONTEND
then you can go to the frontend file and run the html file 

or you can run it through running `Live Server`


![image](https://github.com/z7pz/HLS-encryption-prototype/assets/63007978/fd799e84-4604-430c-85f2-6a924278fcd7)
