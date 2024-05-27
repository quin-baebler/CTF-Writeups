## PicoCTF Writeups

### Intro To Burp
This challenge is an intro to BurpSuite for web exploitation. It involves modifying the one time code being passed through the GET request.

1. Start the instance and open up the website, its a register form so most likely some request is going to be sent when regestering. Copy the Url
Open up BurpSuite and open up the URL (mine was http://titan.picoctf.net:52432/.)
2. I entered in random data in the form and clicked Register, on BurpSuite you can see a POST and GET request that show up when clicking register. After inspecting, there is not much to modify.
3. Next we are on a two factor authentification page, after trying 123456 and submitting we can see we get an invalid OTP page showing up. BUT there is another post request being made.
4. Examining the Post request you can see there is a parameter called OTP that passes the value entered by the user (mine is OPT=123456)
5. We want to change this value to see if we can bypass the OPT, by right clicking and sending to repeater we can send the post request again but changing the parameter, or adding/removing parameters
6. Trying a few more numbers in the repeater by changing the OTP parameter, every one leads to invalid OTP.
7. Finally removing the parameter as a whole we can see we have bypassed the 2FA as a whole and can now see the flag picoCTF{#0TP_Bypvss_SuCc3$S_6bffad21}

This challenge got me started on BurpSuite after I had watched some videos on BugBounties and how BurpSuite works. It was beneficial to see how the repeater works and how requests are shown in BurpSuite

### logon
This challenge is another one with a login form, we use BurpSuite to modify the request 

1. Copy the URL https://jupiter.challenges.picoctf.org/problem/13594/, it consists of a login form
2. Open up Burpsuite and open up the URL 
3. Enter a sample username and password and click enter, I used username and password
4. We get access to the page but it says no flag for you
5. Open the GET request on Burpsuite, in the parameters passed you can see username, password, and admin which is set to false
6. If we send the request to the repeater by right clicking we can modify this request's admin to true and when we resend the request you can see the code picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}

I chose to solve this with BurpSuite to better understand what data is passdd in GET and POST requests and how we can use it to manipulate access

NOTE: You can also find the admin, username, and password in the cookies under the application tab in Chrome inspect
