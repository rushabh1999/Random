
import cv2
import numpy as np

device  =cv2.VideoCapture(0)
while True:
    ret, frame = device.read()
# BLUE
    hsv = cv2.cvtColor(frame,cv2.COLOR_BGR2HSV)
    lower_blue = np.array([100,0,0])
    upper_blue = np.array([130,255,255])
    mask  =cv2.inRange(hsv, lower_blue, upper_blue)
    cv2.imshow("BLUE",mask)
    cv2.imshow("show1", frame)
# RED
    lower_red = np.array([0,0,0])
    upper_red = np.array([15,255,255])
    mask_red  = cv2.inRange(hsv, lower_red, upper_red)
    cv2.imshow("RED",mask_red) 
#GREEN
    lower_green = np.array([40,40,40])
    upper_green = np.array([70,255,255])
    mask_green  = cv2.inRange(hsv, lower_green, upper_green)
    cv2.imshow("GREEN",mask_green)
#PRESS ENTER TO STOP
    if cv2.waitKey(1) ==13 :
        break

device.release()
cv2.destroyAllWindows()
