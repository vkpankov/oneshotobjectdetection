# One-shot object detection methods

**Balanced and Hierarchical Relation Learning for One-shot Object Detection, CVPR 2022**

Main ideas: 
- multi-level relation module IHR ( Instance-level Hierarchical Relation). It learns relation representation to highlight the complex interdependencies for query and target pairs in a hierarchical manner. Three relation levels: contrastive (between global query feature and the local target featur), salient, attention (for learning more detailed local relation)
-  RPL to solve the imbalance issue of positive-negative samples for achieving balanced and effective learning of the IHR module. It dynamically increases the weight of positive samples and decrease the weight of negative samples to retain a suitable and specific number-weighted ratio (neither too big nor too small). The too-small ratio makes the model difficult to learn from positive samples, while the too-large ratio causes overfitting. Moreover, to enhance the learning of false positives, we separate false positives from negative samples. Then, we take false positives and positive samples as a whole to increase their weights and decrease the weights of true negatives

Metrics:
- PASCAL unseen: 73.8% AP
- COCO unseen: 25.6% AP

Code: https://github.com/hero-y/BHRL

**SiamMask, FOC OSOD, AIT (Adaptive image transformer for one-shot object detection. CVPR, 2021)**

Main ideas:
- Two-stage technique is used that relies on the region proposal network (RPN) to generate candidate regions. The original RPN is trained without access to any examples from the unseen object classes, and thus could degrade the detection performance in inference due to excluding some legitimate region proposals for a given one-shot query. In dealing with this issue, multi-head co-attention (MCA) is proposed to correlate the target image and query patch through various embeddings. The attention mechanism jointly considers the target image and the query by exploring different aspects of visual characteristics and spawns a corresponding feature map that encode such relatedness, upon which the RPN could generate more relevant region proposals to the query
- Adaptive Image Transformer (AIT) is proposed to explore how each proposal-query pair shares common semantic attributes over the deep visual features. AIT would adaptively transform the feature map of each proposal to match the query feature via employing the learned attention mechanisms
- Selective channel attention for better proposal ranking (enhancing the importance of channels of high similarity before evaluating a proposal-query pair) (ranking loss)

Metrics: 
- PASCAL unseen: 72.2% AP
- COCO unseen: 24.3% AP

**One-shot object detection with co-attention and co-excitation. NeurIPS, 2019**

Main ideas:
- Non-local object proposals:  enrich feature maps of interest with the non-local operation: use weighted/attended features between target image and the query patch to improve region proposals quality
- Squeeze and co-excitation to emphasize those feature channels that play crucial roles in evaluating the similarity measure (query can flexibly match a candidate proposal by adaptively re-weighting the importance distribution over all channels)
- Proposal ranking:  two-layer MLP network and margin-based ranking loss (encourage most relevant proposals to the query to appear in the top portion of the ranking list)
        
Metrics:
- PASCAL unseen: 63.8% AP
- COCO unseen: 22.0% AP

Code: https://github.com/timy90022/One-Shot-Object-Detection

5. **Towards improving classification power for one-shot object detection. Neurocomputing, 2021**

Main ideas:
- It is shown that a large number of false positives is one of the reasons for the limited performance in the OSOD task
- To solve it, classification Feature Deformation-and-Attention (CFDA) module is proposed to obtain the high-quality query and target features in spatial and channel axis.
- Split Iterative Head (SIH) is proposed to improve the ability to classify similarity between feature generated by CFDA. 

Metrics:
- PASCAL unseen: 71.0% AP
- COCO unseen: 17.5% AP

**Simple Open-Vocabulary Object Detection with Vision Transformers, ECCV, 2022**

Main ideas:
- Large model and extensive image-text pre-training (text-conditioned object detection). Can perform one-shot object detection without modifications by using image-derived instead of text-derived embeddings as queries: supply image- instead of text-derived embeddings as queries to the classification head without modifying the model.
- Contrastively pre-train image and text encoders on large-scale image-text data
- Use Vision Transformer as the image encoder

<img src="images/owlvit.png">The architecture of the proposed method</img>

Metrics:
- COCO: 41.8% AP