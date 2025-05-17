# Dog Breed Identification Web Application

A Flask-based web application that identifies dog breeds from images using a pre-trained ResNet50 model. The application combines local breed database with The Dog API to provide comprehensive breed information, including breed characteristics, history, and similar breed suggestions.

## Features

- Upload images or use image URLs for breed identification
- Compare two dogs side by side
- Advanced image preprocessing:
  - Auto image orientation (EXIF-based)
  - Brightness and contrast adjustment
  - Smart image resizing
- Comprehensive breed information:
  - Temperament and behavior traits
  - Physical characteristics (height, weight)
  - Life expectancy and origin
  - Breed purpose and history
  - Similar breeds with matching characteristics
- Integrated breed data sources:
  - Local database with 13 common breeds
  - The Dog API integration for extended information
  - ResNet50 ImageNet model for classification
- Confidence-based predictions (threshold: 10%)
- Mobile-responsive modern UI

## Requirements

- Python 3.12 or higher
- Flask (Web Framework)
- PyTorch and torchvision (Deep Learning)
- Pillow (Image Processing)
- requests (API Integration)
- Werkzeug (File Handling)
- NumPy (Numerical Operations)

## Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd dog_breed
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # On macOS/Linux
# or
.venv\Scripts\activate     # On Windows
```

3. Install the required packages:

```bash
pip install -r requirements.txt
```

## Configuration

1. Get an API key from [The Dog API](https://thedogapi.com/)
2. Update the `DOG_API_KEY` in `app.py` with your key
3. Ensure the `static/uploads` directory exists (created automatically)
4. Optional: Adjust confidence threshold in `predict_breed()` (default: 10%)

## Running the Application

1. Activate the virtual environment (if not already activated):

```bash
source .venv/bin/activate
```

2. Run the Flask application:

```bash
python app.py
```

3. Open a web browser and navigate to:

```
http://localhost:5000
```

## Usage

### Single Breed Identification

1. On the home page:
   - Click "Choose File" or drag and drop an image
   - Or paste an image URL in the URL field
2. Adjust image preprocessing (optional):
   - Set brightness (0.5 to 1.5)
   - Set contrast (0.5 to 1.5)
3. Click "Identify Breed"
4. View results showing:
   - Top breed predictions with confidence scores
   - Comprehensive breed information
   - Similar breed suggestions
   - Reference breed images (when available)

### Compare Two Dogs

1. Navigate to the Compare tab
2. For each dog:
   - Upload an image
   - Adjust preprocessing settings if needed
3. Click "Compare"
4. View side-by-side comparison showing:
   - Breed predictions for both dogs
   - Detailed breed information
   - Similarities and differences

## Project Structure

```
dog_breed/
├── app.py              # Main Flask application with ML model
├── requirements.txt    # Python package dependencies
├── README.md          # Project documentation
├── static/
│   ├── css/
│   │   └── style.css  # Application styling
│   └── uploads/       # Directory for uploaded images
└── templates/
    ├── index.html     # Home page with upload form
    ├── result.html    # Single breed result display
    └── compare.html   # Two-dog comparison page
```

## Technical Details

### Model Architecture

- Base Model: ResNet50 with IMAGENET1K_V2 weights
- Input Resolution: 224x224 pixels
- Class Range: 151-268 (Dog Breeds)
- Confidence Threshold: 10%

### Image Processing

- Format Support: JPG, JPEG, PNG
- Max File Size: 16MB
- Auto-orientation via EXIF
- Smart resizing (max: 800px)
- Customizable brightness/contrast

### Breed Database

- 13 Common breeds in local cache
- Extended breed info via API
- Characteristics include:
  - Physical traits
  - Temperament
  - Origin and history
  - Breed purpose
  - Similar breeds

## Error Handling

- Invalid file types
- File size limits
- Image processing errors
- API timeouts
- Low confidence predictions
- Missing breed information

## Model Information

The application uses a pre-trained ResNet50 model from torchvision, specifically trained on ImageNet data. It can identify 118 different dog breeds with high accuracy. The model processes images through several steps:

1. Image preprocessing (resizing, normalization)
2. Feature extraction using ResNet50
3. Breed classification with confidence scores
4. Matching with detailed breed information database

## Supported Breeds

The application includes detailed information for many popular breeds including:

- German Shepherd
- Beagle
- Belgian Malinois
- Rottweiler
- Pug
- Labrador Retriever
- French Bulldog
- Golden Retriever
- Siberian Husky
- Dachshund
- Chihuahua


