# 1. Getting App to Run Locally (MacOS)

## Step 1: Install Dependencies
```bash 
# install python requirements
pip install -r requirements.txt

# install OpenCV2
brew install opencv@2

# install Tesseract OCR library
brew install tesseract
```

## Step 2: Clone Repo
```bash
git clone https://github.com/JBRPG/RealTime-TextReaderCamera.git tesseract-letters
```

## Step 3: Run Flask
```bash
cd tesseract-letters
export FLASK_APP=application.py
flask run
# now, navigate to http://127.0.0.1:5000/
```

In order to run the code, you have to ensure that Flask is running. After you get everything installed, you will be able to access your application in the future by just performing Step 3. 


# 2. Getting App to Run on Heroku
1. Create a new app on Heroku
2. Go to the "settings" tab of your application and add the following buildpack:
https://github.com/heroku/heroku-buildpack-apt. This will allow you to install Ubuntu packages (OpenCV, Tesseract, etc.), which can be specified in the Aptfile.
3. For Tesseract, you'll need to create an enviornment variable to point tell the application where the training data is located. Follow [this guide](https://medium.com/@zamhuang/heroku-how-to-install-service-and-setup-environment-variable-use-tesseract-ocr-as-example-d7c708c4ba8d). For my installation, I used the command shown below:

```bash
heroku config:set TESSDATA_PREFIX=/app/.apt/usr/share/tesseract-ocr/4.00/tessdata
```


# 3. Posting Data to Server
Please see `static/js/image-capture.js` and `templates/uploader.html` for examples re: how to transmit an image to the server.
