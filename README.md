# BERT_on_SQuAD
ECE 590-13 Natural Language Processing Final Project   
### Environment Set Up   
- Python modules
BERT only requires tensorflow module. You should have installed version that is equal or greater than 1.11.0.
`tensorflow >= 1.11.0   # CPU Version of TensorFlow.    
tensorflow-gpu  >= 1.11.0  # GPU version of TensorFlow.`
### Colab TPU
- Set up a Colab TPU running environment
- Verify that you are connected to a TPU device.   
`assert 'COLAB_TPU_ADDR' in os.environ, 'ERROR: Not connected to a TPU runtime; please see the first cell in this notebook for instructions!'
TPU_ADDRESS = 'grpc://' + os.environ['COLAB_TPU_ADDR']
print('TPU address is', TPU_ADDRESS)

from google.colab import auth
auth.authenticate_user()
with tf.Session(TPU_ADDRESS) as session:
  print('TPU devices:')
  pprint.pprint(session.list_devices())
  `
  ### Google Cloud Storage
  You should download pre-train BERT models in GCS, otherwise when you fetched data from checkpoints it will raise error.
  - Prepare your output train director in GS bucker
  - Specify BERT pretrained model
  `BUCKET = 'bert_pretrained_model' #@param {type:"string"}
assert BUCKET, 'Must specify an existing GCS bucket name'
OUTPUT_DIR = 'gs://bert_pretrained_model/train_model'
tf.gfile.MakeDirs(OUTPUT_DIR)
print('***** Model output directory: {} *****'.format(OUTPUT_DIR))
l
BERT_MODEL = 'uncased_L-12_H-768_A-12' #@param {type:"string"}
BERT_MODEL_HUB = 'https://tfhub.dev/google/bert_' + BERT_MODEL + '/1'
`
